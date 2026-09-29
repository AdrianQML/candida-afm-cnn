# Hardware and software reference

These measurements describe the active TFQ environment inspected on 2026-09-25.
They do not independently establish which hardware/driver versions were used
for historical timing measurements. Saved experiment evidence agrees on Python
3.11.8, TensorFlow 2.15.0 and Keras 2.15.0.

| Component | Observed value |
|---|---|
| GPU | NVIDIA RTX 5000 Ada Generation Laptop GPU |
| VRAM | 16,376 MiB |
| NVIDIA driver | 596.58 |
| nvidia-smi utility | 595.78 |
| Driver-supported CUDA level | 13.2; not an installed toolkit/runtime version |
| TensorFlow build CUDA | 12.2 |
| TensorFlow build cuDNN | 8; minor/patch not verified by build metadata |
| Installed CUDA runtime | package 12.3.101; library API reports 12.3 |
| Installed cuDNN | package 8.9.7.29; library API reports 8.9.7 |
| System nvcc | CUDA 12.5, V12.5.40 |
| CPU | 13th Gen Intel Core i9-13900H |
| WSL-visible logical CPUs | 20; reported 10 cores × 2 threads |
| WSL-visible RAM | 33,475,416,064 bytes (31.18 GiB) |
| WSL swap | 8 GiB |
| Distribution | Ubuntu 22.04.4 LTS, x86_64 |
| WSL package | 2.7.14.0, WSL2 |
| Running kernel | 6.18.33.2-microsoft-standard-WSL2 |
| WSL-reported Windows version | 10.0.26200.9457 |
| Source Conda environment | TFQ |

Host physical RAM and physical CPU topology were not independently verified;
the CPU and memory counts above are those exposed to WSL. The Python executable
is recorded as observation-only provenance in environment-reference.txt. Users
need not reproduce its absolute path.

TensorFlow runtime library selection during inference and GPU numerical/runtime
compatibility remain unverified because no model was executed. Importing TF
reported duplicate plugin registrations and missing TensorRT. TensorRT is not
imported by these notebooks. Installed NVIDIA versions differ from the optional
TensorFlow and-cuda extra pins; the release specification preserves observed
versions rather than substituting unobserved ones. The CUDA 13.2 driver display
must not be reported as the TensorFlow build or runtime version.

The approximately 31.18 GiB is the memory visible to WSL; it does not establish the laptop's total physical RAM.
