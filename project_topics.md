# Computer Vision — Final Project Topics

**Weight:** 50% of the course grade · **Teams:** ~6 members · **Released:** Week 3 · **Presented:** Week 15

*17 topics.*

Each topic below is scoped for a single consumer GPU or free Colab: fine-tuning pretrained models, small
or subsampled datasets, and inference-time methods. None require training a large model from scratch.

Every topic lists:

- **Core task** — the minimum for a complete, passing project
- **Extensions** — the work that separates a good project from an excellent one
- **Publication angle** — the direction to push if your team wants a workshop paper (talk to me early)
- **Split for 6** — how the work divides so nobody is idle

---

## Group A — Applied systems (build, evaluate, demo)

### 1. Vietnamese traffic scene detection under local conditions

Object detection benchmarks are dominated by Western street scenes. Vietnamese traffic — dense motorbikes,
heavy occlusion, non-standard vehicle types — breaks them.

- **Core task:** collect/curate a few thousand annotated frames, fine-tune YOLO and one DETR-family model, compare mAP by object class and density level.
- **Extensions:** analyze failure modes by crowd density; test-time augmentation; latency-vs-accuracy curves on edge hardware.
- **Publication angle:** a small benchmark dataset plus a failure analysis is a legitimate workshop contribution. Dataset papers are underrated.
- **Split for 6:** 2 data collection/annotation · 2 model training · 1 evaluation harness · 1 analysis and writing.

### 2. Automated visual quality inspection with few defect samples

Real factories have thousands of good parts and a handful of defective ones.

- **Core task:** on MVTec AD, implement and compare three anomaly detection approaches (autoencoder reconstruction, PatchCore-style feature memory, one-class classification).
- **Extensions:** pixel-level defect localization; sensitivity to the number of normal training samples; false-alarm cost analysis.
- **Publication angle:** a systematic study of how each method degrades as normal-sample count drops toward the tens.
- **Split for 6:** 3 one method each · 1 evaluation/metrics · 1 localization · 1 analysis and writing.

### 3. Medical image segmentation with limited annotations

Annotation is the bottleneck in medical imaging — radiologist time is expensive.

- **Core task:** on a public dataset (e.g. polyp, skin lesion, or chest X-ray), compare U-Net trained from scratch, a pretrained encoder, and SAM with prompts.
- **Extensions:** semi-supervised training on unlabeled images; measure performance against annotation budget; inter-observer variability.
- **Publication angle:** annotation-efficiency curves — how much labeled data does each approach actually need to hit clinical usefulness?
- **Split for 6:** 2 baselines · 2 SAM/prompting · 1 semi-supervised · 1 evaluation and writing.
- **Note:** use public de-identified data only. No patient data without ethics approval.

### 4. Real-time sign language or gesture recognition

- **Core task:** build a video classification pipeline (pose keypoints plus a temporal model, or a small video transformer) recognizing 20–50 gestures; run it live from a webcam.
- **Extensions:** signer-independent evaluation (test on people not in training); latency optimization; confusion analysis between visually similar signs.
- **Publication angle:** Vietnamese Sign Language is severely under-resourced. Even a small, well-documented dataset is a contribution.
- **Split for 6:** 2 data/recording · 2 model · 1 real-time pipeline · 1 evaluation and writing.

### 5. Fine-grained plant disease or crop diagnosis

- **Core task:** fine-tune a CNN and a ViT on PlantVillage or a similar dataset; compare accuracy, and test on field photos rather than lab images.
- **Extensions:** quantify the lab-to-field domain gap; augmentation strategies that close it; deploy quantized to a phone.
- **Publication angle:** the lab-to-field generalization gap is real, well-known, and under-measured for specific crops relevant to Vietnam.
- **Split for 6:** 2 training · 1 field data collection · 1 domain-gap analysis · 1 deployment · 1 writing.

---

## Group B — Method comparison and analysis

### 6. What do vision transformers see that CNNs do not?

- **Core task:** take a matched-accuracy ResNet and ViT; compare attention maps, Grad-CAM, effective receptive fields, and robustness to occlusion and texture changes.
- **Extensions:** shape-vs-texture bias experiments; behavior on adversarially cropped images; layer-wise representation similarity (CKA).
- **Publication angle:** careful replication with a new axis of comparison. Analysis papers are publishable and need no large-scale training.
- **Split for 6:** 2 interpretability methods · 2 robustness experiments · 1 representation analysis · 1 writing.

### 7. How far can self-supervised pretraining get you with little labeled data?

- **Core task:** pretrain SimCLR or MAE on an unlabeled subset, then fine-tune with 1%, 10%, and 100% of labels; compare against supervised-from-scratch and ImageNet-pretrained.
- **Extensions:** effect of augmentation choice; does the pretraining domain need to match the target?
- **Publication angle:** label-efficiency curves in a specific applied domain (medical, agricultural, industrial) where nobody has measured them.
- **Split for 6:** 2 pretraining · 2 fine-tuning sweeps · 1 baselines · 1 writing.

### 8. Robustness benchmark: how do modern models actually fail?

- **Core task:** evaluate five pretrained architectures on corrupted inputs (noise, blur, weather, compression) using ImageNet-C-style transforms; produce a robustness ranking.
- **Extensions:** does accuracy on clean data predict robustness? Which corruptions hurt transformers more than CNNs? Does augmentation training help?
- **Publication angle:** extend the corruption suite with distortions specific to a real deployment (motorbike-camera shake, tropical rain, low-light phone cameras).
- **Split for 6:** 2 corruption pipeline · 2 model evaluation · 1 statistical analysis · 1 writing.

### 9. Efficient inference: the accuracy–latency–size frontier

- **Core task:** take one strong model and apply quantization, pruning, and knowledge distillation; plot the accuracy-vs-latency-vs-size trade-off on real hardware.
- **Extensions:** combine techniques; measure on a phone or Raspberry Pi; energy per inference.
- **Publication angle:** an honest, reproducible benchmark on accessible hardware — most published numbers come from datacenter GPUs and don't transfer.
- **Split for 6:** 2 compression techniques · 1 distillation · 1 hardware benchmarking · 1 energy measurement · 1 writing.

### 10. Do detection models transfer across domains?

- **Core task:** train a detector on one domain (e.g. daytime, clear weather) and evaluate on another (night, rain, different city); quantify the drop.
- **Extensions:** domain adaptation methods; how much target-domain data is needed to recover performance; synthetic-to-real transfer.
- **Publication angle:** a domain-shift study on a pairing nobody has published, with a practical "how much data do I need" answer.
- **Split for 6:** 2 training · 2 adaptation methods · 1 evaluation · 1 writing.

### 11. Small object detection

Detectors trained on objects that fill the frame fail on distant ones — the *scale variation* challenge from Lecture 1.

- **Core task:** on VisDrone or AI-TOD, measure how accuracy collapses with object size; compare a detector against high-resolution inference, tiled inference (SAHI-style), and a finer-stride feature pyramid.
- **Extensions:** accuracy gain vs. inference cost of tiling; is the bottleneck stride, label assignment, or loss? Copy-paste augmentation.
- **Publication angle:** decompose *where* the failure happens — detection vs. localization vs. classification as a function of pixel area.
- **Split for 6:** 2 baseline and evaluation · 2 tiling/high-resolution · 1 architecture variant · 1 analysis and writing.

---

## Group C — Generative and multimodal

### 12. Controllable image generation with diffusion models

- **Core task:** use a pretrained Stable Diffusion checkpoint; implement and compare control mechanisms (prompt engineering, ControlNet, image-to-image, inpainting).
- **Extensions:** LoRA fine-tuning on a small custom concept set; evaluate with FID and CLIP score plus a human study.
- **Publication angle:** rigorous evaluation of control fidelity — most claims in this space are demonstrated with cherry-picked examples.
- **Split for 6:** 3 one control method each · 1 LoRA · 1 evaluation/human study · 1 writing.
- **Note:** no training from scratch. Inference and LoRA only.

### 13. Synthetic data for training: does it work?

- **Core task:** generate synthetic training images with a diffusion model for a small classification or detection task; measure whether adding them beats real data alone.
- **Extensions:** find the ratio where synthetic data starts to hurt; which classes benefit most; does it help the rare classes it should?
- **Publication angle:** the point at which synthetic augmentation causes model collapse is an active open question and cheap to study at small scale.
- **Split for 6:** 2 generation · 2 downstream training · 1 ablation design · 1 writing.

### 14. Probing vision–language models

- **Core task:** evaluate CLIP or an open VLM on zero-shot classification across several datasets; systematically test where it fails (counting, spatial relations, negation, fine-grained categories).
- **Extensions:** prompt sensitivity study; does prompt ensembling help; performance on non-English prompts or Vietnamese cultural content.
- **Publication angle:** VLM performance on Vietnamese-language prompts and locally relevant visual concepts is basically unmeasured.
- **Split for 6:** 2 benchmark construction · 2 evaluation · 1 prompt analysis · 1 writing.

### 15. Detecting AI-generated images

- **Core task:** build a classifier distinguishing real photos from diffusion-generated ones; test generalization to a generator not seen during training.
- **Extensions:** which artifacts does it use (frequency domain, texture, faces)? Does JPEG compression or resizing defeat it?
- **Publication angle:** cross-generator generalization is the unsolved part of this problem, and the failure is easy to demonstrate honestly.
- **Split for 6:** 2 dataset assembly · 2 classifier · 1 artifact analysis · 1 writing.

---

## Group D — 3D and video

### 16. From photos to 3D: NeRF and Gaussian splatting in practice

- **Core task:** capture your own object or scene with a phone; reconstruct it with both a NeRF variant and Gaussian splatting; compare quality, training time, and rendering speed.
- **Extensions:** how few input views can you get away with? Sensitivity to capture pattern, motion blur, and lighting change; novel-view quality metrics.
- **Publication angle:** a practical capture guide backed by measurements — how casual can a phone capture be before reconstruction fails?
- **Split for 6:** 2 capture/preprocessing · 2 NeRF · 2 Gaussian splatting, with evaluation and writing shared.

### 17. State space models (Mamba) for video

A 32-frame clip has tens of thousands of tokens — video is where attention's $O(N^2)$ cost bites.

- **Core task:** on UCF-101 or a Kinetics subset, compare a video transformer against VideoMamba across 8- to 64-frame clips; measure accuracy, throughput, and peak memory.
- **Extensions:** scan order — flattening 3D to 1D forces a choice; streaming inference at constant memory, impossible with attention.
- **Publication angle:** published comparisons use datacenter GPUs; repeating them on one consumer GPU, plus the scan-order ablation, is open.
- **Split for 6:** 2 data pipeline · 2 transformer baseline · 2 Mamba model, ablation and writing shared.
- **Note:** `mamba-ssm` compiles CUDA kernels and is version-sensitive.

---


---

## Choosing a topic

**For a solid grade**, pick from Group A. The path to a working system is clear and the risk is low.

**For a publication attempt**, Groups B and C suit you better — analysis and benchmark papers need far less compute
than new architectures, and workshop venues actively want careful negative results. Come talk to me in Week 4 or 5,
not Week 13.

## Deliverables

| Milestone | Week | Content |
|---|---|---|
| Team formation and topic choice | 4 | Team list, ranked topic preferences |
| Proposal | 5 | 2 pages: problem, data, method, evaluation plan, division of work |
| Milestone report | 10 | 3 pages: baseline results, what broke, revised plan |
| Final presentation | 15 | 15 minutes plus questions, all members present |
| Code and report | 15 | Reproducible repository, 6–8 page report in conference format |
