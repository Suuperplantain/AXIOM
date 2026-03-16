# AXIOM

AXIOM is an in-development world-model project focused on building and testing a foundational learning architecture before moving into more advanced application domains. At this stage, the emphasis is on validating core representation-learning behaviour on simpler datasets and controlled inputs rather than deploying a finished end-to-end system.

The current system is centered around learning an internal model of visual data. In practical terms, this means training the model to compress observations into a lower-dimensional latent representation, reconstruct them through a decoder, and use the reconstruction error as a learning signal. This allows the project to test whether the system is forming stable and meaningful internal structure before introducing more complex reasoning, planning, or decision layers.

## Visual Architecture

The diagram below shows the current visual architecture of the VAE training loop used in the project.

![Current VAE Training Loop](docs/vae-training-loop.png)

## Architectural Overview

The implemented architecture is currently organized around the following stages:

- **Data Preparation and Caching**  
  Input data is preprocessed into a more efficient cached format to support repeatable experiments and reduce training overhead.

- **Encoding / Representation Learning**  
  An encoder processes observations and maps them into a compact latent space. This latent representation is intended to capture the most relevant structural features of the dataset while reducing raw input complexity.

- **Latent Space Formation**  
  The latent layer acts as the model’s compressed internal state. Rather than working directly on raw observations, the system learns to represent data in a form that is easier to store, compare, and reconstruct.

- **Decoding / Reconstruction**  
  A decoder reconstructs the observation from the latent representation. This provides a direct way to evaluate whether the internal representation preserves meaningful information.

- **Loss-Based Feedback Loop**  
  The reconstruction is compared with the original input, and the resulting loss is used to update the model. This creates the training loop that gradually improves the encoder-decoder pair.

- **Latent Export and Reuse**  
  Latent statistics can be exported into an intermediate format so learned representations can be reused beyond the initial training pass.

- **Memory-Oriented Reconstruction Stage**  
  A separate decoding stage can be trained from stored latent outputs, allowing the project to test how well learned internal representations can function as a reusable memory layer.

## Development Focus

This repository should currently be understood as an experimental architecture in progress. The immediate objective is to confirm that the model can learn useful internal representations, preserve them in latent form, and reconstruct meaningful structure from them with reasonable stability.

At the present stage, the project is mainly exploring questions such as:

- can the model learn a compact and consistent internal representation of the dataset,
- can that representation be exported and reused without retraining the full pipeline,
- and can the reconstruction process confirm that the latent space is capturing meaningful information rather than noise

Higher-level modules will be introduced only after the representation, memory, and reconstruction pipeline has been tested thoroughly enough to serve as a reliable foundation.

## Project Status

AXIOM is currently a work in progress. The architecture is still evolving, and the repository is intended to document the direction of the system while development continues.
