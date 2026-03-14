# AXIOM

This project is currently in development and is being built from the ground up as a world-model style system. At its current stage, the focus is not on final application logic, but on developing and testing the underlying learning architecture on simpler datasets and controlled inputs first.

The current architecture is centered on representation learning. The system is designed to first build a visual understanding of input data by compressing observations into a lower-dimensional latent space, then reconstructing and reusing those latent representations through a separate memory-oriented decoding stage. This makes it possible to test whether the model is learning meaningful structure from the dataset before higher-level reasoning or decision layers are introduced.

## Current Architecture

The implemented pipeline is split into a few core stages:

- **Data Preparation and Caching**  
  Raw input data is prepared into a more efficient cached format so repeated training runs can be carried out more consistently and with less overhead.

- **Encoding / Representation Learning**  
  An encoder is trained to process visual inputs and map them into a compact latent representation. This stage is intended to capture the most important structural features of the dataset in a compressed form.

- **Latent Export Layer**  
  After encoding, latent statistics are exported into an intermediate format so they can be reused independently of the original training pass.

- **Decoding / Memory Reconstruction**  
  A decoder is then trained on the latent outputs so the system can reconstruct observations from its learned internal representation. This acts as an early memory mechanism and helps evaluate whether the latent space contains useful and recoverable information.

## Development Direction

At the moment, this repository should be viewed as an early experimental architecture rather than a finished system. The goal right now is to validate the core world-model pipeline on simpler tasks before extending it into more advanced domains.

In other words, the project is currently focused on questions like:
- can the model learn a stable internal representation of the dataset,
- can that representation be stored and reused effectively,
- and can the decoder recover meaningful structure from the learned latent space.

Higher-level modules are still under development and will be introduced only after the foundational encoding, memory, and reconstruction pipeline has been tested properly.

## Project Status

This project is a work in progress. The architecture is still being refined, and the repository is currently intended to document the direction and structure of the system while development continues.
