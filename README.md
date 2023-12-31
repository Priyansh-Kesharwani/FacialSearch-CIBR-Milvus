# Facial-Image-Search-Engine-CIBR-with-Milvus
<p align="center">
  <img src="https://miro.medium.com/v2/resize:fit:828/0*GibgcYb8tARyAwBZ" width="600" height="200">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c6/PyTorch_logo_black.svg/2560px-PyTorch_logo_black.svg.png" width="600" height="200">
</p>

## Overview

This repository contains an implementation of a robust facial image search engine using Milvus, an open-source vector database. This application allows for fast and accurate searches for similar face images based on deep-learned facial embeddings.

## Application Architecture

The application consists of two key components:

1. **Facial Encoder**: This component generates semantic vector embeddings for face images using deep learning models.

2. **Milvus Search Index**: It performs efficient similarity search and retrieval on the facial vectors.
3. **Attu**: Provides monitoring, alerts, and insights for Milvus.

## Facial Encoder

The facial encoder follows these steps to create a 512-dimensional embedding vector for each face image:

1. **Face Detection**: Utilizes MTCNN (via facenet-pytorch) to identify and crop facial regions.

2. **Feature Extraction**: The cropped faces are passed through a pretrained InceptionResnetV1 model from VGGFace2 to output feature vectors.

3. **Embedding Generation**: The model embeddings are processed to generate the final 512-dimensional float vectors.


## Milvus Setup
<p align="center">
  <img src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*uN0CIKZYydOpTNYK5vhOPw.png" width="600" height="200">
</p>

Milvus provides the vector index and search capabilities for the application. The following steps are used to set up Milvus:

1. Install Milvus server locally or on cloud infrastructure.

2. Create a Milvus collection called 'face_search' with appropriate fields.

3. Define an IVF_FLAT index on the embedding vector field for efficient search.

4. Insert facial vectors from the encoder into the Milvus collection.

5. Optimize index parameters like `nlist` for optimal performance.

## Configuring Attu
<p align="center">
   <img src="https://milvus.io/static/2d8c1d0da0fc8af1df342d2f55b292a9/6ffd1/insight_overview.png" width="600" height="200">
</p>
Once Milvus is set up, Attu can be configured for monitoring and visibility:

1. Install Attu agent on the Milvus server.

2. Configure a data source to point to the Milvus instance.

3. Set up desired alerts and monitoring metrics.

4. Customize dashboards and views as needed.

5. Review Attu insights to optimize Milvus performance.


## Search Pipeline

To perform a search, a query image passes through the facial encoder to generate its embedding vector. This vector is used to query Milvus:

1. Connect to the Milvus server and access the 'face_search' collection.

2. Pass the query embedding to Milvus' vector similarity search.

3. Retrieve the top N closest matches based on the Euclidean distance of vectors.

4. Return image filenames/metadata associated with matched face vectors.


This facial image search engine combines state-of-the-art deep learning with Milvus' purpose-built vector search capabilities. It can reliably scale to billions of face images for applications like de-duplication and identity search.




