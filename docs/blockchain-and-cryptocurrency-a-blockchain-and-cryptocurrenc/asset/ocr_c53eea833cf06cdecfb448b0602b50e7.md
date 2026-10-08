```
$ sudo apt update
$ sudo curl -0
https://storage.googleapisapis.com/golang/go1.9.2.linux-amd64.tar.gz
```

**Note:** Switch out the black portion of the URL with the correct filename.

```
$ sudo tar -xvf go1.9.2.linux-amd64.tar.gz
$ sudo mv go /usr/local
$ echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.profile
$ source ~/.profile
```

Check that the Go version is v1.8 or later:

```
$ go version
```

# 24.10 Installing Hyperledger Fabric Docker Images and Binaries

Next, we will download the latest released Docker images for Hyperledger Fabric and tag them with the latest tag. Execute the command from within the directory into which you extract the platform-specific binaries:

```
$ curl -sSL https://go.gl/6wtTN5 | bash -s 1.1.0
```

NOTE: Check http://hyperledger-fabric.readthedocs.io/en/release-1.1/samples#binaries for the latest URL (the blue portion in the above curl command) to pull in binaries.

This command downloads binaries for cryptogen, configtxgen, configxlator, peer and downloads the Hyperledger Fabric