# Object Identification System

**Project Plan and Documentation**
University Project | Beginner-Friendly | Zero-Budget, CPU-Only Design

---

## Original Request

Prepare a complete project plan for a project named Object Identification System. Explain its purpose, working, objectives, scope, and real-world applications. Identify all required data types, datasets (COCO, ImageNet, Open Images), databases, pre-trained models (YOLO, MobileNet, Faster R-CNN), programming languages, technologies, frameworks, and free development resources. Also explain system architecture, project requirements, possible challenges, risks, solutions, and estimated budget. Keep everything beginner-friendly, prefer free resources, assume no GPU or investment, and do not write any code. Prepare professional project documentation suitable for a university project.

---

## 1. Project Overview

### 1.1 Purpose

The Object Identification System (OIS) is a software application that looks at an image or a video and automatically finds the objects in it, such as people, cars, chairs, cups, or animals. For every object it finds, it draws a box around it, names it (for example, "dog"), and gives a confidence score (for example, 91%).

The purpose of the project is to show how modern computer vision can be built by a student using only free tools, free datasets, and an ordinary laptop, by reusing pre-trained deep learning models instead of training everything from scratch.

### 1.2 Problem Statement

People and organizations need computers that can "see." Doing this manually (a person watching every image or camera feed) is slow, expensive, and error-prone. Training a vision model from zero requires large datasets and expensive GPUs. This project solves the problem by combining ready-made models with a simple, usable application that runs on a normal computer without a GPU.

### 1.3 How the System Works (Plain-Language Explanation)

1. **Input:** The user uploads a photo, selects a video, or turns on a webcam.
2. **Preparation:** The system resizes the image and adjusts its colors and numbers into the format the model expects.
3. **Detection:** A pre-trained neural network scans the image. It has learned from millions of labeled pictures what everyday objects look like. It proposes boxes where it believes objects are.
4. **Classification and scoring:** For each box, the model decides which object it is and how sure it is.
5. **Cleaning up:** Overlapping duplicate boxes are merged, and low-confidence guesses are dropped.
6. **Output:** The system shows the image with labeled boxes, a list of detected objects with counts, and optionally saves the results to a database or file.

An easy analogy: the model is like a person who has studied millions of flashcards. When shown a new picture, they point at things and say what they are, based on experience rather than fixed rules.

---

## 2. Objectives

### 2.1 Main Objective

To design, build, test, and document a working CPU-only system that identifies and locates common objects in still images using free tools. Video and webcam support are optional extensions.

### 2.2 Specific Objectives

- Understand the core ideas of image classification and object detection.
- Build an image-detection MVP using one small, pre-trained model and a simple upload interface.
- Evaluate the chosen detector on a fixed, labeled test subset and report accuracy and CPU speed reproducibly.
- Optionally compare a second detector or add video/webcam input if the MVP is complete.
- Save results locally and document the model, dataset, and software versions used.
- Produce complete university-level documentation and a final demonstration.

### 2.3 Success Criteria (Measurable)

| Criterion | Target |
| --- | --- |
| Core input | Upload and process still images |
| Classes | The classes supported by the selected pre-trained model; document its label set |
| Works with no GPU | Yes; record the test computer specifications |
| Speed on CPU | Measure and report; do not assume a universal speed target |
| Accuracy | Report COCO-style mAP and a defined precision/recall result on a labeled test subset |
| Optional extensions | Video/webcam input or a second model, only after the MVP works |
| Cost | $0 for the core project |

---

## 3. Scope

### 3.1 In Scope

- **Required MVP:** detect and label objects in still images using one small pre-trained detector, with a simple local interface.
- **Required MVP:** display confidence scores and object counts, and report processing time.
- **Optional extensions:** recorded video or webcam input, a second model comparison, local result export/storage, or fine-tuning a small custom dataset.
- Evaluate on a fixed, labeled subset that is small enough for the available computer.
- Complete documentation, testing, and a final presentation.

### 3.2 Out of Scope

- Training a large model from scratch.
- Real-time performance on high-resolution multi-camera feeds.
- Mobile app publishing and cloud deployment at scale.
- Face recognition and identity tracking (privacy-sensitive).
- Safety-critical use (medical diagnosis, autonomous driving decisions).

### 3.3 Assumptions

- The student has a laptop or desktop with a CPU, about 8 GB RAM (4 GB minimum), and an internet connection.
- The student has basic computer skills and will learn Python step by step.
- Free online tools (Google Colab, Kaggle) are available for any heavier experiments.

---

## 4. Real-World Applications

| Field | Example Use |
| --- | --- |
| Retail | Counting products on shelves, detecting empty shelves, self-checkout assistance |
| Traffic and transport | Counting vehicles, detecting pedestrians, helmet or lane monitoring |
| Security | Spotting unattended bags or unauthorized objects in restricted areas |
| Agriculture | Counting fruit, detecting pests or diseased leaves |
| Healthcare support | Locating items in lab or hospital images (research use) |
| Manufacturing | Quality inspection, detecting missing parts on a production line |
| Accessibility | Describing surroundings for visually impaired users |
| Smart homes | Detecting packages at the door, pets, or people in a room |
| Wildlife and environment | Camera-trap animal counting, litter detection |
| Education | Interactive learning tools and science demos |

---

## 5. Data Requirements

### 5.1 Data Types Needed

| Data Type | Description | Use in Project |
| --- | --- | --- |
| Images (JPG, PNG) | Still photos of scenes with objects | Main input and testing data |
| Video (MP4, AVI) and webcam streams | Sequences of frames | Real-time/recorded detection demos |
| Annotations (labels) | Files describing the box location and class of each object (formats such as COCO JSON, Pascal VOC XML, YOLO text) | Evaluation and fine-tuning |
| Class label lists | Names of the categories (person, car, dog, etc.) | Displaying readable results |
| Model weight files | Saved knowledge of pre-trained models | Running detection |
| Results data (structured) | Detected class, confidence, box position, time, file name | Logging, statistics, reports |
| Configuration data | Settings such as confidence threshold | Tuning behavior |

### 5.2 Datasets

| Dataset | What It Contains | Size (approximate) | Best Use in This Project | Notes |
| --- | --- | --- | --- | --- |
| **COCO** (Common Objects in Context) | Everyday scenes with boxes and masks for 80 object classes | About 330,000 images, about 1.5 million object instances | Main reference. Most pre-trained detectors are trained on it; use its validation set for testing | Free; permissive, citation-friendly licensing for annotations; images come from Flickr with their own licenses |
| **Open Images** | Very large, diverse set with boxes for about 600 classes | Millions of images (over 9 million), about 16 million boxes | Source of extra classes and extra test images; download only the classes you need | Free; use the class-filtered downloader to avoid huge downloads |
| **ImageNet** | Images labeled by a single category across about 1,000 classes | About 1.28 million training images | Understanding classification; MobileNet backbones are pre-trained on it | Mainly classification, not detection boxes; registration required and intended for non-commercial research and education; the full dataset is very large, so you will not download it |

**Beginner recommendation:** Do not download full datasets. For the MVP, choose a fixed, labeled subset small enough for your computer and verify that both the images and annotations are permitted for your intended use. COCO is a suitable detector-evaluation source; ImageNet is primarily a classification dataset and should not be presented as a source of detection boxes. Record the subset and annotation version so the evaluation can be repeated.

### 5.3 Optional Small Custom Dataset

If your university wants a custom touch (for example, detecting "helmets" or "bottles"), collect 200-500 of your own photos and label them using a free labeling tool. Fine-tuning a small model on this is possible on free cloud notebooks.

---

## 6. Databases

| Option | Type | Why Consider It | Cost |
| --- | --- | --- | --- |
| **SQLite** (recommended) | File-based relational database | No installation or server, built into Python, ideal for student projects | Free |
| **CSV / JSON files** | Flat files | Simplest option for very small projects | Free |
| **PostgreSQL** | Relational server database | Optional upgrade for multi-user or larger data | Free (open source) |
| **MongoDB** (free community or free cloud tier) | Document database | Handy if you prefer flexible JSON-like records | Free tier |

**Suggested tables (conceptual):**

- *Images:* file name, upload time, source.
- *Detections:* image reference, class name, confidence, box position, model used.
- *Runs/Experiments:* model name, settings, accuracy and speed results.

---

## 7. Pre-Trained Models

A pre-trained model is a neural network already trained by researchers on huge datasets, so you can use it immediately without training it yourself.

### 7.1 Comparison

| Model | Type | Strengths | Weaknesses | CPU Suitability |
| --- | --- | --- | --- | --- |
| **YOLO** (You Only Look Once; for example YOLOv5, YOLOv8, or newer nano/small versions) | One-stage detector | Fast, good accuracy, very easy to use, ready-made COCO weights, simple tools | Can miss very small or crowded objects; check the license terms of the version you use (some are AGPL-3.0) | Good with the smallest ("nano"/"small") versions |
| **MobileNet** (usually used as MobileNet-SSD or SSDLite) | Lightweight network, designed for phones and low-power devices | Very small and fast, low memory, perfect for weak computers | Lower accuracy than larger models | Excellent |
| **Faster R-CNN** | Two-stage detector | Very accurate, good with small objects, a classic model for research comparison | Slow, heavier, needs more memory | Possible but slow; best used on small test sets or in free cloud notebooks |

### 7.2 Recommended Strategy

- **MVP:** choose one small, COCO-pretrained detector and get image inference and evaluation working end to end. A small YOLO variant is one reasonable candidate; confirm its current license and requirements before selecting a specific release.
- **Optional comparison:** add one alternative, such as a MobileNet-SSD detector, only after the MVP is stable. Faster R-CNN is a possible research comparison, but is not required for the beginner CPU-only scope.
- Keep the exact model name, weight source, version, and license in the report. Compare models on the same images and document any model-specific settings.

---

## 8. Programming Languages, Technologies, and Frameworks

### 8.1 Programming Language

- **Python** (primary): beginner-friendly, huge community, most computer vision tools are built for it.
- **HTML/CSS/JavaScript** (optional): only if you want a custom web front end; not required.

### 8.2 Libraries and Frameworks

| Purpose | Tool | Why |
| --- | --- | --- |
| Image and video handling | OpenCV | Standard free library for reading, drawing on, and processing images and video |
| Deep learning | PyTorch or TensorFlow/TFLite | Run and fine-tune models; PyTorch is common for YOLO and Faster R-CNN, TFLite for MobileNet |
| Model hub | Ultralytics, TorchVision, TensorFlow Hub | Provide ready-made pre-trained models |
| Efficient CPU inference | ONNX Runtime or OpenVINO | Speeds up models on ordinary CPUs |
| Data handling | NumPy, Pandas | Arrays, tables, statistics |
| Charts and reports | Matplotlib | Accuracy and speed graphs |
| User interface | Streamlit (recommended for the MVP); Gradio is an alternative | Build a small local image-upload interface |
| Data labeling (optional) | LabelImg, CVAT, Label Studio, Roboflow free tier | Mark objects in your own images |
| Evaluation | COCO evaluation tools (pycocotools) | Calculate mAP in the standard way |

### 8.3 Development Tools

- **Editor:** Visual Studio Code or Jupyter Notebook.
- **Environment management:** Python virtual environments or Anaconda/Miniconda.
- **Version control:** Git with GitHub.
- **Documentation:** Google Docs/Word, draw.io for diagrams.

---

## 9. Free Development Resources (No GPU Strategy)

### 9.1 Free Compute

| Resource | What You Get | Best For |
| --- | --- | --- |
| **Your own CPU** | Full local development | Running the MVP, building the app, and demos |
| **Google Colab (free tier)** | Browser-based notebook, free GPU access on a limited, non-guaranteed basis | Short fine-tuning and testing experiments |
| **Kaggle Notebooks** | Free GPU/TPU with a weekly usage quota (check the current limit) and free datasets | Longer experiments and storing datasets |
| **GitHub Codespaces / Gitpod (free tiers)** | Cloud development environments | Working from any computer |

### 9.2 Free Learning Resources

- Official documentation of Python, OpenCV, PyTorch, TensorFlow, and Ultralytics.
- Free courses: Kaggle Learn (Python, Computer Vision), fast.ai, Coursera/edX (audit mode), Stanford CS231n lecture materials, and YouTube tutorials on object detection.
- Research papers (free on arXiv): YOLO, SSD/MobileNet, Faster R-CNN, COCO dataset paper.
- Communities: Stack Overflow, GitHub Issues, Reddit r/computervision, university forums.

### 9.3 Tips for Working Without a GPU

1. Use a small model and pre-trained weights; do not train from scratch for the MVP.
2. Keep the test subset and image size small enough for local CPU evaluation.
3. Measure performance on the target computer before considering optimizations such as ONNX, OpenVINO, or TFLite.
4. Treat video frame skipping and cloud fine-tuning as optional extensions, not MVP dependencies.
5. Test on small subsets before running larger experiments.

---

## 10. System Architecture

### 10.1 Architecture Overview (Layered Design)

The system follows a simple pipeline with five layers:

```text
[1. Input Layer]
  Image upload | Video file | Webcam
        |
        v
[2. Pre-processing Layer]
  Resize, color conversion, normalization, frame sampling
        |
        v
[3. Detection Layer (AI Engine)]
  Pre-trained model (YOLO / MobileNet-SSD / Faster R-CNN)
  -> boxes + class names + confidence scores
        |
        v
[4. Post-processing Layer]
  Remove duplicate boxes, apply confidence threshold,
  draw boxes and labels, count objects
        |
        v
[5. Output and Storage Layer]
  User interface display | Saved images/videos | Database (SQLite) | Reports
```

### 10.2 Component Descriptions

| Component | Responsibility |
| --- | --- |
| User Interface | Lets the user choose input, pick a model, set the confidence level, and view results |
| Input Handler | Reads images, video frames, or webcam frames |
| Pre-processor | Converts each image into the exact format the model needs |
| Model Manager | Loads the chosen pre-trained model and runs it |
| Post-processor | Filters results and prepares the annotated output |
| Storage Module | Saves detection records and result files |
| Evaluation Module | Computes accuracy and speed statistics on the test set |

### 10.3 Data Flow Summary

User input goes to the pre-processor, then to the model, then to the post-processor, then to the display and database. The evaluation module reads stored results and compares them against the ground-truth labels of the test set.

### 10.4 Suggested Diagrams for Your Report

Draw these with the free tool draw.io: a block diagram of the layers above, a use-case diagram (user uploads image, selects model, views results, exports report), a data flow diagram, and an entity-relationship diagram of the database tables.

---

## 11. Project Requirements

### 11.1 Functional Requirements

| ID | Requirement |
| --- | --- |
| FR1 | The system shall accept an image, a video file, or a live webcam stream. |
| FR1 | The MVP shall accept a still image. Video and webcam input are optional extensions. |
| FR2 | The system shall detect objects and show boxes, class names, and confidence scores. |
| FR3 | The user shall be able to choose between at least two models. |
| FR3 | The MVP shall run one documented pre-trained model. Selecting a second model is an optional extension. |
| FR4 | The user shall be able to adjust the confidence threshold. |
| FR5 | The system shall display a count of each detected object type. |
| FR6 | The system shall save results (images and records) on request. |
| FR6 | The MVP shall display results. Saving images or records is an optional extension. |
| FR7 | The system shall display performance information such as processing time. |
| FR8 | The system shall export a summary report (for example, CSV). |
| FR8 | Exporting a summary (for example, CSV) is an optional extension. |

### 11.2 Non-Functional Requirements

| Category | Requirement |
| --- | --- |
| Performance | Acceptable speed on a CPU-only computer |
| Usability | Simple interface that a first-time user can operate without training |
| Reliability | Does not crash on unsupported or corrupt files; shows clear error messages |
| Portability | Runs on Windows, macOS, or Linux |
| Maintainability | Clean, modular, documented structure |
| Privacy | Images are processed locally and not shared with outside services |
| Cost | Entirely free and open-source tools |

### 11.3 Hardware Requirements

| Item | Minimum | Recommended |
| --- | --- | --- |
| Processor | Dual-core CPU | Quad-core i5/Ryzen 5 or better |
| RAM | 4 GB | 8 GB or more |
| Storage | 10 GB free | 20-30 GB free |
| GPU | Not required | Not required |
| Webcam | Optional | Any basic webcam (or use a phone camera) |
| Internet | For setup and downloads | Stable connection |

### 11.4 Software Requirements

- Windows 10/11, macOS, or Linux.
- Python 3.9 or newer, with the libraries listed in Section 8.
- A modern web browser (Chrome, Firefox, or Edge).
- Git, and a code editor such as VS Code.

---

## 12. Project Plan and Timeline (12 Weeks)

| Phase | Weeks | Activities | Deliverables |
| --- | --- | --- | --- |
| 1. Study and planning | 1-2 | Learn Python basics and the idea of object detection; finalize scope; set up tools | Approved proposal, working environment |
| 2. Data and model study | 3-4 | Select one pre-trained detector; verify its license and requirements; prepare a small labeled test subset | Dataset/model notes, first detection results |
| 3. Core system development | 5-7 | Build and test the still-image pipeline: input, pre-processing, detection, and display | Working image-detection MVP |
| 4. Interface and optional storage | 8 | Add a simple local interface; add result storage only if time permits | Usable MVP, optional storage |
| 5. Testing and evaluation | 9-10 | Run the fixed evaluation protocol, measure CPU speed, and fix bugs; compare a second model only if the MVP is stable | Reproducible test report |
| 6. Documentation and presentation | 11-12 | Finalize report, diagrams, user manual, slides, and demo video | Final report and presentation |

---

## 13. Testing and Evaluation Plan

### 13.1 Metrics (Explained Simply)

| Metric | Meaning |
| --- | --- |
| Precision | Of the objects the system reported, how many were correct |
| Recall | Of the objects actually present, how many the system found |
| IoU (Intersection over Union) | How well the predicted box overlaps the true box |
| mAP (mean Average Precision) | The standard overall accuracy score for detectors |
| FPS / seconds per image | Speed |
| Memory use | RAM consumed while running |

### 13.2 Reproducible Evaluation Protocol

1. Record the test computer's CPU, RAM, operating system, Python version, and relevant library versions.
2. Record the exact model and weight version, image size, confidence threshold, and any other inference settings.
3. Use a fixed, labeled test subset and retain its source, annotation version, and selected image IDs. Do not tune settings on this test subset.
4. Report the mAP definition used (for example, COCO mAP@[.5:.95]) and the evaluation tool/version. Define the confidence threshold and matching rule used for any precision/recall figures.
5. Measure inference time on the same images and hardware for every model. State whether timing includes image loading and pre/post-processing; report the number of images and a summary such as mean and median.
6. If comparing another model, use the same test images and report its model-specific settings and licensing separately.

### 13.3 Test Types

- **Functional testing:** Does image upload, detection, result display, and error handling work? Test save/export only if those optional features are implemented.
- **Accuracy testing:** Evaluate on the fixed labeled subset using the protocol above.
- **Performance testing:** Record speed on your CPU for the selected model; compare another model only if implemented.
- **Robustness testing:** Try dark, blurry, crowded, and tiny-object images.
- **Usability testing:** Ask 3-5 classmates to use it and give feedback.

---

## 14. Challenges, Risks, and Solutions

### 14.1 Technical Challenges

| Challenge | Why It Happens | Solution |
| --- | --- | --- |
| Slow processing on CPU | No GPU acceleration | Use nano/small models, lower image size, skip frames, use ONNX/OpenVINO/TFLite |
| Low accuracy on small or blurry objects | Limited resolution and lightweight models | Use higher resolution for key tests, use Faster R-CNN for comparison, document limits honestly |
| False detections | Model confuses similar objects | Raise the confidence threshold and report errors in analysis |
| Poor performance in bad lighting or odd angles | Training data differs from your test conditions | Test across conditions, optionally fine-tune with a small custom dataset |
| Limited memory | Large models and datasets | Use dataset subsets and small models; close other programs |
| Software setup problems | Version conflicts between libraries | Use virtual environments and note exact versions |
| Fine-tuning needs a GPU | Training is heavy | Use free Colab/Kaggle sessions and save checkpoints often |

### 14.2 Project Risks

| Risk | Likelihood | Impact | Mitigation |
| --- | --- | --- | --- |
| Free cloud GPU unavailable or session times out | Medium | Medium | Keep the core project CPU-only; treat cloud work as optional; save progress frequently |
| Large dataset downloads fail or exceed storage | Medium | Medium | Download small subsets only; use Kaggle-hosted copies |
| Falling behind schedule due to the learning curve | Medium | High | Follow the timeline; start with ready-made models; ask the supervisor early |
| Laptop failure or data loss | Low | High | Back up code to GitHub and documents to cloud storage weekly |
| Dataset or model licensing misunderstandings | Low | Medium | Read the license of each dataset and model; cite them; keep the project non-commercial |
| Scope creep (adding too many features) | Medium | Medium | Freeze the scope after Week 2; list extras as "future work" |
| Poor results that look like failure | Medium | Low | Treat honest evaluation and analysis as the goal; explain the causes |

### 14.3 Ethical and Legal Considerations

- **Privacy:** Avoid uploading images of people without permission; do not implement face recognition.
- **Bias:** Public datasets may not represent every region or culture equally; mention this in your limitations.
- **Licensing:** Cite datasets and models properly; respect non-commercial terms (especially ImageNet).
- **Misuse:** State clearly that the system is for educational purposes and not for surveillance or critical decisions.

---

## 15. Estimated Budget

### 15.1 Core Project (Zero-Investment Path)

| Item | Tool | Cost |
| --- | --- | --- |
| Programming and libraries | Python, OpenCV, PyTorch/TensorFlow | $0 |
| Pre-trained models | YOLO, MobileNet-SSD, Faster R-CNN | $0 |
| Datasets | COCO, Open Images, ImageNet (subsets) | $0 |
| Database | SQLite | $0 |
| Interface | Streamlit or Gradio | $0 |
| Cloud compute (optional) | Google Colab and Kaggle free tiers | $0 |
| Code hosting | GitHub free | $0 |
| Diagrams and documents | draw.io, Google Docs | $0 |
| Learning materials | Official docs, free courses, YouTube | $0 |
| Hardware | Your existing computer | $0 |
| **Total** | | **$0** |

### 15.2 Hidden or Indirect Costs

| Item | Estimate |
| --- | --- |
| Internet data for downloads (a few GB) | Small, depends on your plan |
| Electricity and printing of the report | Minimal |
| Your time | About 8-12 hours per week for 12 weeks |

### 15.3 Optional Paid Upgrades (Not Needed)

These are listed for completeness only. The project is fully achievable without them.

| Item | Approximate Cost | When It Would Help |
| --- | --- | --- |
| Colab Pro or similar paid GPU plan | About $10 per month | Longer or more reliable fine-tuning |
| Extra storage (USB drive or cloud) | $5-$20 | Large datasets and backups |
| External webcam | $15-$30 | Better live demo quality |
| Cloud hosting for a public demo | $5-$10 per month | Sharing the app online |

---

## 16. Expected Deliverables

1. Working Object Identification System (source code on GitHub).
2. Project report (this document, extended with results).
3. Evaluation report with metrics and graphs; include a model comparison if a second detector is implemented.
4. User manual with screenshots.
5. Demo video (2-3 minutes).
6. Final presentation slides.

---

## 17. Future Enhancements

- Object tracking across video frames and counting people or vehicles crossing a line.
- Detection of custom objects through fine-tuning.
- Segmentation (outlining the exact shape of objects).
- A mobile or browser-based version using lightweight models.
- Voice output that describes the scene for accessibility.
- Deployment on a low-cost device such as a Raspberry Pi.

---

## 18. Conclusion

The Object Identification System demonstrates that a useful, modern computer vision application can be built by a beginner at no cost and without a GPU. By reusing pre-trained models (YOLO, MobileNet, Faster R-CNN) and public datasets (COCO, Open Images, ImageNet), the project focuses on understanding, integration, evaluation, and responsible use rather than expensive training. The result is a practical, well-documented system with clear academic value.

---

## 19. References (Starting Points)

## 19. Selected References

### Datasets

- Lin, T.-Y., et al. (2014). "Microsoft COCO: Common Objects in Context." *European Conference on Computer Vision (ECCV).* [arXiv:1405.0312](https://arxiv.org/abs/1405.0312)
- Kuznetsova, A., et al. (2020). "The Open Images Dataset V4: Unified Image Classification, Object Detection, and Visual Relationship Detection at Scale." *International Journal of Computer Vision.* [arXiv:1811.00982](https://arxiv.org/abs/1811.00982)
- Russakovsky, O., et al. (2015). "ImageNet Large Scale Visual Recognition Challenge." *International Journal of Computer Vision.* [arXiv:1409.0575](https://arxiv.org/abs/1409.0575)

### Model Papers

- Redmon, J., et al. (2016). "You Only Look Once: Unified, Real-Time Object Detection." *IEEE Conference on Computer Vision and Pattern Recognition (CVPR).* [arXiv:1506.02640](https://arxiv.org/abs/1506.02640)
- Howard, A. G., et al. (2017). "MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications." [arXiv:1704.04861](https://arxiv.org/abs/1704.04861)
- Liu, W., et al. (2016). "SSD: Single Shot MultiBox Detector." *European Conference on Computer Vision (ECCV).* [arXiv:1512.02325](https://arxiv.org/abs/1512.02325)
- Ren, S., et al. (2015). "Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks." *Advances in Neural Information Processing Systems (NeurIPS).* [arXiv:1506.01497](https://arxiv.org/abs/1506.01497)

### Official Documentation

- COCO dataset: [cocodataset.org](https://cocodataset.org/)
- Open Images dataset: [official dataset site](https://storage.googleapis.com/openimages/web/index.html)
- ImageNet: [image-net.org](https://www.image-net.org/)
- Ultralytics documentation: [docs.ultralytics.com](https://docs.ultralytics.com/)
- PyTorch: [pytorch.org](https://pytorch.org/docs/stable/)
- OpenCV: [docs.opencv.org](https://docs.opencv.org/)
- Streamlit: [docs.streamlit.io](https://docs.streamlit.io/)
- SQLite: [sqlite.org](https://www.sqlite.org/docs.html)

Before final submission, cite the exact software and model releases used, and verify current dataset/model licenses and service quotas on their official sites.
