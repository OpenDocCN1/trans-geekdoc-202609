Assume you’re using Docker Desktop on an M3 Mac where Docker runs inside a linux/arm VM. You ask Docker to pull an image, and Docker makes the relevant calls to the Registry API to request the appropriate manifest list. Assuming it exists, Docker then parses a linux/arm entry. If linux/arm entry exists, Docker retrieves its manifest, parses it for the crypto IDs of its layers, pulls each individual layer, and assembles them into the image.

Let's see it in action.

The following examples are from Docker Desktop on an ARM-based Mac and Docker Desktop on an AMD-based Windows machine running in Windows containers mode. Both start a new container based on the official golang image and execute the version command. The outputs show the version of Go and the host's platform and CPU architecture. Notice how both commands are exactly the same, and Docker takes care of pulling the correct image.

Both images are large and may take a while to download. You do not need to complete these commands yourself.

Linux on arm64 example: