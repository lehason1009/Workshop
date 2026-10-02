---
title : "Build Docker Image"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.6.1. </b> "
---

## Build Docker Image

CloudCV is packaged in an image based on Python 3.12. Docling requires document-processing libraries and layout models, so the image installs CPU-only PyTorch and preloads the required models.

---

## Create the Dockerfile

The project Dockerfile installs Python dependencies, copies the source, and prepares the Docling models in the image. The report does not include the full Dockerfile, so use the version in the source repository rather than copying an unrelated example.

---

## Build the Docker Image

After creating the Dockerfile, open a terminal in the project root directory and build the Docker image.

Run the following command.

```bash
docker build -t cloudcv .
```

Docker performs the following operations during the build process:

1. Downloads a Python 3.12 base image if needed.
2. Installs the API and Docling dependencies, including CPU-only PyTorch.
3. Copies the source and preloads the layout-analysis models.
4. Packages the service as a Docker image.

When the build completes successfully, Docker displays a message similar to the following.

```text
Successfully built <IMAGE_ID>
Successfully tagged cloudcv:latest
```

To verify that the image was created successfully, run:

```bash
docker images
```

The command displays all Docker images stored on the local machine. Confirm that the newly created image appears in the list with the **latest** tag.

---

## Expected Result

After completing this section, you will have:

- The `cloudcv:latest` image builds successfully.
- The container can start without downloading Docling models on first launch.