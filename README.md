### 📌 Project Goal
---

**Dragonfly Analyzer** is a tool that automatically compiles and generates statistical reports based on field observations of dragonflies.  
It is intended to support biologists and ecologists who work with indicator species — species whose populations are particularly sensitive to environmental changes.

The program processes Excel files ([sample data file](_datafiles/1_Calopteryx%20splendens.xlsx)) containing species data and generates a summary report.

📊 The summary report includes:
* Total number of individuals
* Count per year
* Count per grid square
* Yearly population trends
* Average temperature, cloud cover, and wind speed:
    * by year
    * by grid square
    * yearly trends
* Predominant observed water conditions
* Water condition trends
* Predominant observed shading level
* Shading trends

The program automates routine calculations and report structure creation, allowing specialists to focus on data interpretation and enabling the use of results in more advanced analysis stages such as TWINSPAN classification.

The report can be saved in three different formats: **JSON**, **XML**, or **Excel**, depending on the user's choice ([example output](_datafiles/results)).

The project was created as a solution to a real-world problem — helping a fellow researcher speed up data preparation for their bachelor’s thesis in biology.

### 🐍 Python Libraries Used in Development
---

#### 📦 Third-party libraries:
* `pandas` — for working with data tables; used to load and process Excel data.
* `openpyxl` — for reading/writing Excel files with formatting.
* `Pillow` — used for image handling in the graphical interface.

#### 🧰 Standard Python modules:
* `pathlib` — for path and file structure handling.
* `numbers` — for checking and validating numerical types.
* `re` — for regular expressions (e.g., filename parsing).
* `multiprocessing` — used to parallelize GUI updates and file operations.
* `tkinter` — for the graphical user interface.
* `dataclasses` — used for the `@dataclass` decorator in `Node` classes.
* `os` — for file system interactions.
* `typing` — for type annotations.
* `time` — for measuring execution time.
* `xml` — for exporting data in `XML` format.
* `json` — for serializing and input/output of data in `JSON` format.

### 🧱 Custom Data Structures Used
---

* `HashTable` — a custom data structure replicating `dict` behavior. Its size increases dynamically when the load reaches 70%, ensuring efficiency with large datasets.
* `ProcessSafeQueue` — a custom structure that mimics `multiprocessing.Queue`. Used for data exchange between the GUI process and the file-processing process. Internally uses a `LinkedList` to ensure `O(1)` complexity for dequeue operations. When 1000 spent elements accumulate and the queue holds no useful data, it is cleared. Also includes a custom exception `EmptyProcessSafeQueueError` raised when attempting to get data from an empty queue.

---

#### 🧩 Other Key Program Components

* `DragonflyAnalyzer` — the main class responsible for compiling data, calculating results, and generating the summary.
* `Dragonfly` — represents a single dragonfly species and stores related statistics.
* `ErrorCollector` — collects all errors that occur during execution, aiding in debugging.
* `UICommandHandler` — handles GUI events, validates input data, and launches the file-processing subprocess.
* `WidgetManager` — manages `tkinter` widgets, organizing layout and interface structure.
* `Tooltip` — a custom tkinter widget that replicates the behavior of the HTML `title` attribute.
* `StyleManager` — loads styles from a `JSON` file and converts them into a `ttk.Style` object.
* `FileWriter`, `JsonWriter`, `XmlWriter` — classes responsible for outputting data to `JSON` and `XML` files.

### 🖥️ How to Use the Program
---

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
2. Launch the program using the command line:
    ```bash
    python app/main.py
3. A graphical interface built with tkinter will open.
4. The interface includes the following features:
* Select output file format (Excel, XML, JSON)
* Add Excel files
* Start analysis
* View logs for progress and errors
* After execution, the program processes the files and saves the results to the user-selected location on the computer.

### 🔮 Alternative Method (Windows Only)
---

1. Click on `windows_run.bat`

2. The batch script will:
   - Check if Python is installed and verify its version
   - Check for required dependencies and install them if needed

3. If all checks succeed, the graphical interface will open automatically!

### License
---

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

### Authors
---

<p align="center"><strong>Co-developed with <a href="https://github.com/neimee8/">@neimee8</a>.</strong> Synchronized copy <a href="https://github.com/neimee8/dragonfly_analyzer">here</a>.</p>
