# asleep: a sleep classifier for wearable sensor data using machine learning
I made a few minor hardcoded adjustments to ensure this classifier runs on NHANES 2011–2014 data.

This is a Python package for classifying sleep stages from wearable sensor data / wrist - worn accelerometer. The underlying model
was trained and tested in 1000 + nights of multi - centre polysomnography with tri - axial accelerometer data.

The key features of this package are as follows:
* A simple and easy - to - use API for sleep stage classification.
* Sleep / wake metric estimation including total sleep duration and sleep efficiency.
* Sleep architecture metric estimation including rapid - eye - movement(REM) / NREM sleep duration.


![](https://raw.githubusercontent.com/OxWearables/asleep/main/assets/figure.jpg)


# Dependencies
- Python 3.8
- Java 8 (1.8.0) or greater

# Installation
```bash
$ conda create -n asleep python=3.8 openjdk pip
$ conda activate asleep 
$ pip install asleep
```

# Usage
All the processing will be much faster after the first time because the model weights will to have to be downloaded
the first time that the package is used.
```shell

# CSV file (see data format below)
$ get_sleep sample.csv
```

Output
```shell
Summary
-------
{
    "Filename": "sample.csv",
    "Device": ".csv",
    "Filesize(MB)": 2272.8,
    "SampleRate": 77,
    "LowpassOK": 1,
    "LowpassCutoff(Hz)": 20,
    "CalibNumSamples": 29396,
    "CalibErrorBefore(mg)": 14.849037863314152,
    "CalibErrorAfter(mg)": 3.347760997712612,
    "CalibNumIters": 33,
    "CalibOK": 1,
    "CalibxIntercept": -0.022534770891070366,
    "CalibyIntercept": 0.015741821378469467,
    "CalibzIntercept": -0.008018394000828266,
    "CalibxSlope": 0.9971864223480225,
    "CalibySlope": 0.9986444711685181,
    "CalibzSlope": 1.0008964538574219,
    "ResampleRate": 30,
    "NumTicksAfterResample": 20753067,
    "WearTime(days)": 8.006584104930555,
    "NonwearTime(days)": 0.0,
    "NumNonwearEpisodes": 0,
    "StartTime": "2000-01-08 12:30:00",
    "EndTime": "2000-01-16 12:39:28"
}

Output: outputs /sample/
```

# Visualisation
You can visualise the sleep parameters using the following command:
This now works with --remove_intermediate_files
```shell
$ visu_sleep PATH_TO_OUTPUT_FOLDER
```
![sleep](https://github.com/user-attachments/assets/e72770ca-a3ac-42f6-924f-028d2c2210d8)


# Processing CSV files
I hardcoded the CSV processing to ONLY work with NHANES files.
The CSV file must have the following headers: HEADER_TIMESTAMP, X, Y, Z.
Example:
```shell
HEADER_TIMESTAMP,X,Y,Z
2000-01-08 12:30:00.000,0.856,0.164,0.34
2000-01-08 12:30:00.013,0.859,0.173,0.416
2000-01-08 12:30:00.025,0.801,0.173,0.446
2000-01-08 12:30:00.038,0.771,0.205,0.443
2000-01-08 12:30:00.050,0.856,0.182,0.334
2000-01-08 12:30:00.063,0.865,0.194,0.37
2000-01-08 12:30:00.075,0.853,0.238,0.399
2000-01-08 12:30:00.088,0.894,0.217,0.308
2000-01-08 12:30:00.100,0.886,0.267,0.396
```

# Please remember to cite the original paper and author—they did a fantastic job!
```bibtex
@article{yuan2024self,
  title={Self-supervised learning of accelerometer data provides new insights for sleep and its association with mortality},
  author={Yuan, Hang and Plekhanova, Tatiana and Walmsley, Rosemary and Reynolds, Amy C and Maddison, Kathleen J and Bucan, Maja and Gehrman, Philip and Rowlands, Alex and Ray, David W and Bennett, Derrick and others},
  journal={NPJ digital medicine},
  volume={7},
  number={1},
  pages={86},
  year={2024},
  publisher={Nature Publishing Group UK London}
}
```

# Acknowledgements
We would like to thank all our code contributors, manuscript co - authors, and research participants for their help in making this work possible. The
data processing pipeline of this repository is based on the [step_count](https://github.com/OxWearables/stepcount) package from our group. Special
thanks to @chanshing for his help in developing the package.
