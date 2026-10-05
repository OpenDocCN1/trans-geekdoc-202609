
You can configure a new swarm to use an external CA by passing the --external-ca flag to docker swarm init command, and you can use the docker swarm ca command to manage other CA-related settings.

```
$ docker swarm ca --help

Usage: docker swarm ca [OPTIONS]

Display and rotate the root CA

Options:
  --ca-cert pem-file      Path to the PEM-formatted root for the new cluster
  --ca-key pem-file       Path to the PEM-formatted new cluster
  --cert-expiry duration Validity period for node certificate (default 2160h0m0)
  -d, --detach           Exit immediately instead of waiting to converge
  --external-ca external-ca Specifications of one or more ca
  -q, --quiet            Suppress progress output
  --rotate               Rotate the swarm CA - if no ca is provided, new ones will be generated
```

## The cluster store

The cluster store is where Docker keeps the configuration and state of a swarm. It’s also critical to other Docker technologies, such as overlay networks and secrets. This is why overlay networks and many other advanced security features only work in swarm mode.

The cluster store is based on the popular etcd distributed database and is automatically encrypted and replicated to all managers.

Docker handles day-to-day maintenance, but you should implement strong backup and recovery procedures for production clusters.

That's enough about swarm mode security for now. Let's look at some Docker security technologies that don't require swarm mode.

## Docker Scout and vulnerability scanning

Every container runs multiple software packages that are susceptible to bugs and vulnerabilities that malicious actors can exploit.

Image scanning analyzes your images and produces a detailed list of all the software packages it uses. We call this list a software bill of materials (SBOM), and the image scanning system compares the SBOM against databases of known vulnerabilities and provides a report of vulnerabilities in your software. Most vulnerability scanners will rank the vulnerabilities and provide advice on fixes.

Vulnerability scanning is now an integral part of most software supply chains.

**Docker Scout** is Docker’s native scanning platform and works with Docker Hub, Docker Desktop, the Docker CLI, and even has its own Docker Scout Dashboard. However, it’s a subscription-based service.

Other scanning platforms are available, but most of these also require some form of subscription.

If you’re using Docker Desktop, you can run the following command to see an example of Docker Scout.

```
$ docker scout quickview nigelpoulton/tu-demo:latest

✓ Provenance obtained from attestation
✓ Pulled
✓ Image stored for indexing
✓ Indexed 66 packages

| Target | nigelpoulton/tu-demo:latest | 0C |
| :--- | :--- | :--- |
| digest | b4210d0aa52f | |
| Base image | python:3-alpine | 0C |
| Updated base image | python:3.11-alpine | 0C |
```

The output shows zero critical vulnerabilities (0C), four high (4H), two medium (2M), and zero low (0L).

You can also run a docker scout cves command to get more detailed information, including remediation advice.

```
$ docker scout cves nigelpoulton/tu-demo:latest

✓ SBOM of image already cached, 66 packages indexed
✓ Detected 6 vulnerable packages with a total of 8 vulnerabilities
## Overview
Analyzed Image

| Target | nigelpoulton/tu-demo:latest
| :--- | :--- |
| digest | b4210d0aa52f |
| platform | linux/arm64 |
| vulnerabilities | 0C 4H 2M 0L |
| size | 26 MB |
| packages | 66
## Packages and Vulnerabilities
0C 1H 1M 0L expat 2.5.0-r2
pkg:apk/alpine/expat@2.5.0-r27os_name=alpine&os_version=3.14

* HIGH CVE-2023-52425
https://scout.docker.com/v/CVE-2023-52425
Affected range : <2.6.0-r0
Fixed version : 2.6.0-r0

* MEDIUM CVE-2023-52426
https://scout.docker.com/v/CVE-2023-52426
Affected range : <2.6.0-r0
Fixed version : 2.6.0-r0
<Snip>
```

I've snipped the output, so it only shows some of the vulnerabilities. However, even from the snipped output in the book, you can see:

- Scout has scanned 66 packages and detected several vulnerabilities
- We’re using version 2.5.0-r2 of the expat package which has one high (1H) and one medium (1M) vulnerability
- The high vulnerability is listed as CVE-2023-52425 and the medium as CVE-2023-52426
- The report includes links to Scout reports containing more info on each vulnerability
- Scout recommends updating to expat version 2.6.0-r0 which contains fixes for both

Figure 16.8 shows what it looks like in Docker Desktop, and you get similar integrations and views in Docker Hub.

![](img/aae0230bf8529bd80767c4c780dca8d3_453_0.png)

If you subscribe to Docker Scout, you can use the scout.docker.com portal to configure policies and integrations with Docker Hub and other registries.

As good as vulnerability scanning, is, it only scans images and doesn't detect security problems with networks, nodes, or orchestrators. Also, not all scanners are equal. For example, the best ones perform deep binary-level scans, whereas others may just look at package names and do not inspect content closely.

In summary, scanning tools are great for inspecting your images and detecting known vulnerabilities. Beware though, with great knowledge comes great responsibility — once you’re aware of vulnerabilities, you’re responsible for mitigating or fixing them.

## Signing and verifying images with Docker Content Trust

Docker Content Trust (DCT) makes it simple for you to verify the integrity and publisher of images and is especially important when you're pulling images over untrusted networks such as the internet.

At a high level, DCT lets you sign your images when you push them to registries like Docker Hub. It also lets you verify the images you pull and run as containers.

Figure 16.9 shows the high-level process.

![](img/aae0230bf8529bd80767c4c780dca8d3_455_0.png)

Figure 16.9 - Docker Content Trust image signing and verification

You can also use DCT to provide *context*, such as whether or not a developer has signed an image for use in a particular environment such as **prod** or **dev**, or whether an image has been superseded by a newer version and is therefore stale.

The following steps walk you through configuring Docker Content Trust, signing and pushing an image, and then pulling the signed image.

If you plan on following along, you'll need a cryptographic key pair. If you don't already have one, you can run the following **docker trust** command to generate one. The command generates a new key pair called **nickel** and loads it to the local trust store ready for use. It will prompt you to enter a passphrase; don't forget it :-)

```
$ docker trust key generate niger
Generating key for niger...
Enter passphrase for new niger key with ID 1f78609
```
If you already have a key pair, you can import it with **docker trust key load**. The next step is associating your key pair with the repository to which you'll push images. This example associates the **niger.pub** key with **nigpoun/ddd-** repo on Docker Hub. Your file and repo will be different, and the repository doesn't have to exist before you run the command.

```
$ docker trust signer add --key niger.pub niger nigpoun/ddd-
Adding signer "niger" to nigpoun/dct...
Initializing signed repository for nigpoun/dct...
Enter passphrase for root key with ID aee3314:
Enter passphrase for new repository key with ID 1a18dd1:
Repeat passphrase for new repository key with ID 1a18dd1:
Successfully initialized "nigpoun/dct"
Successfully added signer: niger to nigpoun/dct
```

Now that you've loaded the key pair and associated it with a repository, the final step is to sign an image and push it to the repo.

The following command signs a local image called **nigelpoulton/ddd-trust:signed** and pushes it to Docker Hub. Your image will have a different name and you'll push it to a different repo.

```
$ docker trust sign nigelpoulton/ddd-trust:signed
Signing and pushing trust data for local image nigelpoulton/ddd-t
The push refers to repository [docker.io/nigelpoulton/ddd-trust]
6495b414566f:7ef8b: Mounted from nigelpoulton/ddd-book
79867f7ef8b: Mounted from nigelpoulton/ddd-book
bca2a409639: Mounted from nigelpoulton/ddd-book
28ad2149d870: Mounted from nigelpoulton/ddd-book
4f4fb700ef54: Mounted from nigelpoulton/ddd-book
5elfc7f5df34: Mounted from nigelpoulton/ddd-book
signed: sha256:b65f91aa4e670bbafad0fbb91281ea95f9cdc7528a
Signing and pushing trust metadata
Enter passphrase for nigel key with ID 92330ea:
Successfully signed docker.io/nigelpoulton/ddd-trust:signed
```

The push operation creates the repo on Docker Hub and then signs and pushes the image. You can view the repo on Docker Hub, and you can run the following command to inspect its signing data.

```
$ docker trust inspect nigelpoulton/ddd-trust:signed --pretty

Signatures for nigelpoulton/ddd-trust:signed
```
