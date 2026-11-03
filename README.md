# VisionForge AI

### Custom Object Detection with YOLO11

VisionForge AI is a computer vision project that trains and evaluates a
custom object detection model using **Ultralytics YOLO11**. The Jupyter
Notebook automates dataset preparation, creates a YOLO data
configuration, trains a model, runs predictions on validation images,
and packages the trained weights and training outputs.

> **Dataset note:** The notebook expects a custom image dataset provided
> as `data.zip`, together with a `classes.txt` file containing one class
> name per line. The specific object categories and dataset source are
> not identified in the notebook.

## Project Workflow

1.  **Extract the dataset** --- Unzip `data.zip` into
    `/content/custom_data`.
2.  **Create train/validation split** --- Download and run the
    `train_val_split.py` utility, using a 90% training split.
3.  **Install Ultralytics** --- Install the package used to train and
    run YOLO object detection.
4.  **Generate `data.yaml`** --- Read class names from `classes.txt` and
    write the dataset configuration.
5.  **Train YOLO11** --- Train `yolo11s.pt` for 100 epochs with an image
    size of 480.
6.  **Run inference** --- Predict on images in the validation image
    folder using the best saved checkpoint.
7.  **Review predictions** --- Display up to 30 saved prediction images
    in the notebook.
8.  **Package model artifacts** --- Copy the best checkpoint and
    training directory into `my_model`, then create `my_model.zip`.

## Model Configuration

  Setting                 Value used in the notebook
  ----------------------- -------------------------------------
  Task                    Object detection
  Framework               Ultralytics
  Model checkpoint        `yolo11s.pt`
  Training epochs         100
  Image size              480
  Training split          90%
  Validation split        10%
  Prediction checkpoint   `runs/detect/train/weights/best.pt`

## Tech Stack

-   Python
-   Jupyter Notebook / Google Colab
-   Ultralytics YOLO11
-   PyYAML
-   ZIP utilities
-   `train_val_split.py` dataset-splitting utility

## Repository Structure

A suggested repository layout:

``` text
VisionForge-AI/
├── ML_project.ipynb
├── data.zip                  # Custom dataset (if permitted to share)
└── README.md
```

Generated folders such as `runs/`, `custom_data/`, and `my_model/` are
created during notebook execution and do not need to be committed unless
you intend to publish those artifacts.

## Getting Started

### 1. Open the notebook

Upload `ML_project (1).ipynb` to Google Colab or open it in a Jupyter
environment configured for shell commands.

### 2. Prepare the dataset

Place `data.zip` in the notebook's expected working location. The
archive should contain the image and annotation structure required by
the dataset-splitting utility.

Create `classes.txt` with one class name on each line. For example:

``` text
class_one
class_two
class_three
```

Replace these example labels with the actual classes in your dataset.

### 3. Run the notebook

Run the cells in order. The notebook extracts the dataset, prepares the
split, installs Ultralytics, generates `/content/data.yaml`, and starts
training.

### 4. Review predictions and model output

After training, the notebook runs inference on the validation images and
displays saved prediction images. It then packages the best model
checkpoint and training output into:

``` text
/content/my_model.zip
```

## Output Artifacts

-   **Best model weights:** `runs/detect/train/weights/best.pt`
-   **Prediction images:** `runs/detect/predict/`
-   **Packaged checkpoint:** `my_model/my_model.pt`
-   **Training results:** `my_model/train/`
-   **ZIP package:** `my_model.zip`

## Important Notes

-   The notebook uses Google Colab-style paths under `/content/`; adapt
    paths if running locally.
-   The dataset archive and `classes.txt` must be supplied separately.
-   The dataset must include compatible object-detection annotations.
    The notebook does not document the dataset's exact source or class
    names.
-   Training time and model performance depend on dataset size,
    annotation quality, and available hardware.
-   No accuracy or performance result is claimed here because the
    notebook does not include recorded evaluation metrics.
    
------------------------------------------------------------------------

If you find this project useful, consider giving the repository a ⭐.
