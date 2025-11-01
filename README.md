# RiceCooker-Assembly-Dataset

This repository contains a custom dataset for rice cooker assembly monitoring, designed for hand tracking, object detection, and action recognition in manufacturing tasks. It serves as the data foundation for the **Video Assembly Monitor** project, which integrates YOLO for real-time detection and EOID (a Vision-Language Model) for zero-shot semantic analysis.

For the main model pipeline and full system integration, see: https://github.com/Yunchen-Cai/Real-Time-Manual-Assembly-Monitor-YOLO-EOID

---

## 📦 Dataset Overview

This dataset was constructed to address limitations in existing benchmarks like Assembly101, providing multi-view videos, spatial/temporal annotations, and documentation specific to rice cooker assembly. It supports training and evaluation of models for verifying assembly steps, detecting errors, and optimizing efficiency.

Key features:
- Multi-perspective views (front, operator, left-side, right-side) for comprehensive coverage.
- Annotations for objects (e.g., hands, screws, base) and actions (e.g., handling, insertion).
- Includes correct/wrong order demos for sequence validation.

---

## 🗂️ Dataset Structure

The dataset is organized into the following folders and files:

- **annotation_files/**: Supporting documentation and strategies.
  - future_work.docx: Ideas for future dataset improvements.
  - media_rice_cooker_book.pdf: Reference manual for rice cooker parts and assembly.
  - roboflow_annotation_strategy.docx: Guide on using Roboflow for annotation.

- **RicecookerDataset/**: Core dataset files.
  - annotations/: JSON/TXT files with bounding boxes and labels (YOLO format).
  - images/: Extracted frames from videos for object detection.
  - 2024.12.15annotated.mp4: Annotated assembly video.
  - assembly_quota.xlsx: Excel file with quotas, timings, and standard operating times (SOT) for each step.
  - assembly_sequence.docx: Detailed step-by-step assembly sequence.
  - disassembly_sequence.pdf: Guide for reverse assembly processes.

- **via-annotation/**: Outputs from VGG Image Annotator (VIA) for temporal annotations.
  - demo/: Demonstration files.
  - VIA_Project_06Nov2024_16h36m06s.export.csv: Exported annotations in CSV format.
  - VIA_Video_Annotator_2024-10-23_17-42-57.mp4: Annotated video (1).
  - VIA_Video_Annotator_2024-10-23_17-44-59.mp4: Annotated video (2).
  - via_project_06Nov2024_16h33m56s.json: VIA project JSON file.
  - via_project_version2.json: Updated version of the VIA project JSON.

Large files (e.g., MP4 videos) are managed via Git LFS for efficient download.

---

## 🚀 Usage

This dataset is optimized for integration with YOLO and EOID models in the main project. Here's how to use it:

1. **Clone the Repository**:
   ```
   git clone https://github.com/Yunchen-Cai/RiceCooker-Assembly-Dataset.git
   cd RiceCooker-Assembly-Dataset
   ```

2. **Install Git LFS (if not already)**:
   - To download large files:
     ```
     git lfs install
     git lfs pull
     ```

3. **Prepare for Model Training**:
   - **For YOLO**: Use annotations/ and images/ from RicecookerDataset/. Import into Roboflow for preprocessing/augmentation, then train via Ultralytics YOLO scripts.
   - **For EOID**: Use VIA JSON exports for temporal data. Adapt formats with transfer.py from the main repo (https://github.com/Yunchen-Cai/Real-Time-Manual-Assembly-Monitor-YOLO-EOID).
   - Reference assembly_sequence.docx for predefined steps and SOT.

4. **Example Workflow**:
   - Load videos (e.g., via-annotation/*.mp4) with OpenCV.
   - Annotate/validate using Roboflow or VIA tools.
   - Train models: See main repo's setup section for YOLO/EOID scripts.
   - Evaluate: Use demos for correct/wrong sequences to test order verification.

For full integration, clone the main repo and link this dataset as input.

---

## 📜 License

MIT License - see LICENSE file.

---

## 📖 Citation

If using this dataset, cite:  
Cai Yunchen, "RiceCooker-Assembly-Dataset", GitHub, 2025.

For questions or contributions, open an issue on GitHub.
