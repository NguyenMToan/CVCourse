# Computer Vision — Course Materials

Lecture slides, figures and hands-on notebooks for a 15-week Computer Vision course.

**Nguyen Manh Toan — Swinburne Vietnam**

Every number quoted on a slide is computed rather than copied from a paper. If a slide says a speed-up is
8.7×, there is a line of NumPy here that produced 8.7.

---

## The 15 weeks

### Part 1 — Foundations

| # | Topic | Slides | Notebook | Figures |
|---|---|---|---|---|
| 1 | Introduction & image formation | *(not in this repo)* | — | — |
| 2 | Classical image processing | 69 pp | 59 cells | 32 |
| 3 | Image classification & linear models | 63 pp | 59 cells | 18 |
| 4 | From neural networks to CNNs | 43 pp | 40 cells | 17 |

### Part 2 — Core architectures

| # | Topic | Slides | Notebook | Figures |
|---|---|---|---|---|
| 5 | CNN architectures | 45 pp | 36 cells | 10 |
| 6 | Vision transformers | 46 pp | 51 cells | 14 |
| 7 | Object detection I | *planned* | — | — |
| 8 | Object detection II | *planned* | — | — |

### Part 3 — Dense prediction

| # | Topic | Slides | Notebook | Figures |
|---|---|---|---|---|
| 9 | Segmentation | *planned* | — | — |
| 10 | Pose estimation & faces | *planned* | — | — |
| 11 | Video & motion | *planned* | — | — |

### Part 4 — Modern topics

| # | Topic | Slides | Notebook | Figures |
|---|---|---|---|---|
| 12 | Self-supervised learning | *planned* | — | — |
| 13 | Generative models | *planned* | — | — |
| 14 | 3D vision & emerging topics | *planned* | — | — |
| 15 | Project presentations | — | — | — |



## Building

### Requirements

Python 3.10+ with:

```
numpy  scipy  matplotlib  scikit-learn  scikit-image  opencv-python
```

Optional, for the final section of each notebook: `torch`, `torchvision`.


### Slides


---

## The notebooks

Each is self-contained, runs top to bottom, and follows the same shape: numbered sections
mirroring the lecture, cells marked **TODO** for students to complete, a PyTorch section at
the end, and open-ended exercises.


---

## Assessment & logistics

Teams of ~6. Project topics released **Week 3**, proposals due **Week 5**, mid-term
**Week 9**, presentations **Week 15**.

| Component | Weight |
|---|---|
| Project | 50% |
| Mid-term | 40% |
| Participation | 10% |

Each lecture ends with a 30-minute hands-on session using that week's notebook.

The mid-term in Week 9 falls at the end of Part 3's first lecture, so it covers Parts 1–2
and segmentation — everything through the core architectures. Part 4 is assessed through
the project rather than examined.
