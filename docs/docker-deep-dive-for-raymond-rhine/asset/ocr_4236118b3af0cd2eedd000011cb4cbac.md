# Chapter summary

This chapter taught you the important theory and fundamentals of images.

You learned that images contain everything needed to run an application as a container. This includes just enough OS, source code, dependencies, and metadata.

You can start one or more containers from a single image.

Under the hood, Docker constructs images by stacking one or more read-only layers and presenting them as a unified object. Every image has a manifest that lists the layers that make up the image and how to stack them.

You learned that image names are also called tags, they're mutable, and they don't always pull the same image. For example, pulling the alpine:latest tag today will not pull the same image as it will in a year from now. Fortunately, every image gets an immutable digest that you can use to guarantee you always pull the same image.

Docker Hub has the notion of curated official images that should be safer to use than unofficial images. However, you should