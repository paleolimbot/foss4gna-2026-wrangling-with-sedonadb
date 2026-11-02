# Wrangling uncomfortably large spatial data on your laptop with Python and SedonaDB

...slightly reimagined as *An introduction to spatial databases with SedonaDB*.

## Instructions

You can run the workshop locally in VS Code or in a browser using GitHub
Codespaces. Choose one setup below. Bring a laptop and charger, and make sure
you can connect to the venue Wi-Fi.

### Local setup

1. Download and install [Visual Studio Code](https://code.visualstudio.com/download)
   for your operating system. Install [Python](https://www.python.org/downloads/)
   as well if it is not already available on your computer. VS Code and Python
   are separate installations.
2. Open [the workshop repository](https://github.com/paleolimbot/foss4gna-2026-wrangling-with-sedonadb)
   in your browser. Select the branch specified by the instructor, or leave it
   on `main` if none is specified. Click **Code → Download ZIP**.
3. Unzip the downloaded file into a folder where you want to keep your workshop
   work. On Windows, right-click the ZIP and choose **Extract All**; on macOS,
   double-click it. Extract the files before opening them in VS Code.
4. Launch VS Code and choose **File → Open Folder…**. Select the extracted
   repository folder containing `README.md`, `requirements.txt`, and the
   notebooks. Open that whole folder, rather than an individual notebook.
5. In VS Code's **Extensions** view, install the Microsoft **Python** and
   **Jupyter** extensions.
6. Open the **Command Palette** with **Cmd+Shift+P** (macOS) or
   **Ctrl+Shift+P** (Windows/Linux). Run **Python: Create Environment**, choose
   **Venv**, and select your Python interpreter. Follow the prompts to create
   `.venv` in the repository. When prompted for a requirements file, select
   `requirements.txt` to install the workshop packages, including `ipykernel`.
7. If you skipped package installation during environment creation, run
   **Python: Select Interpreter** and select `.venv`, then choose
   **Terminal → New Terminal**. VS Code should activate the environment in the
   new terminal. From the repository folder, run:

   ```sh
   python -m pip install -r requirements.txt
   ```

8. Open [00-hello-sedona-db.ipynb](00-hello-sedona-db.ipynb). Click
   **Select Kernel** at the top right (or the current kernel name), choose
   **Select Another Kernel → Python Environments** if needed, and select
   `.venv`.
9. Run the first code cell and check that a table of state boundaries appears.
   Then run the download cell to get the places dataset described below.

For additional help, see the [VS Code setup guide](https://code.visualstudio.com/docs/getstarted/overview),
[Python environment guide](https://code.visualstudio.com/docs/python/environments),
and [GitHub ZIP download instructions](https://docs.github.com/en/repositories/working-with-files/using-files/downloading-source-code-archives).

### GitHub Codespaces Setup

This option runs in your browser. You do not need to install Python
or VS Code on your laptop.

1. Create a [personal GitHub account](https://github.com/signup), or sign in to
   your existing account. Make sure you can complete any two-factor
   authentication on the day.
2. Open [the workshop repository](https://github.com/paleolimbot/foss4gna-2026-wrangling-with-sedonadb).
   Click **Code → Codespaces → Create codespace** on the workshop branch. You do
   not need to fork the repository first. Start with the default 2-core machine
   unless the instructor specifies otherwise.
3. Wait for the environment setup to finish. It installs Python dependencies
   and the Python and Jupyter extensions automatically, then opens
   `01-introduction.ipynb` in the browser editor.
4. If prompted to select a notebook kernel, choose **Python Environments** and
   select the workshop's `.venv` environment (Python 3.12). If another kernel is
   already selected, click its name at the top right to change it.
5. Open [00-hello-sedona-db.ipynb](00-hello-sedona-db.ipynb), run the first code
   cell, and check that a table of state boundaries appears. Then run the
   download cell to get the places dataset described below.

### Workshop data (both setups)

The state and county boundary files, `data/tiger_state.parquet` and
`data/tiger_county.parquet`, are included in the repository and its ZIP download.
The larger places dataset is downloaded separately by the final cell in
[00-hello-sedona-db.ipynb](00-hello-sedona-db.ipynb). Allow roughly 410 MB of disk
space for `data/us_places.parquet` and wait for the download to finish before
running the joins notebook.

### At the workshop

For local setup, reopen the extracted repository folder in VS Code. For
Codespaces, return to [Your Codespaces](https://github.com/codespaces) and reopen
the environment you already tested. Reuse your existing Codespace rather than
creating a new one each time.

### Codespaces usage and cleanup

Personal GitHub accounts include a monthly Codespaces allowance. GitHub Free
currently includes 120 core-hours (60 running hours on a 2-core machine) and
15 GB-month of storage. Check your remaining allowance before the workshop if
you already use Codespaces. Payment details are not required to use the included
allowance; see [GitHub's Codespaces information](https://github.com/features/codespaces)
and [billing documentation](https://docs.github.com/en/billing/concepts/product-billing/github-codespaces).

Stop your Codespace when you finish: closing the browser tab does not stop it
immediately. Stopped Codespaces still use storage allowance. After the workshop,
download any notebooks you want to keep (right-click the file in the Explorer
and choose **Download**), or commit and push your work to your own fork, before
deleting the Codespace from [Your Codespaces](https://github.com/codespaces).
See [stopping and starting a Codespace](https://docs.github.com/en/codespaces/developing-in-a-codespace/stopping-and-starting-a-codespace).

## Original Session Description

Learn how analytical databases make the most of your laptop to make existing workflows faster and larger workflows possible using SedonaDB, a database built for spatial from the ground up.

It’s not just you...working with large spatial datasets in Python is awkward. Examples include data that is too big to fit into memory, too big to fit comfortably on a local hard drive, or takes minutes to even load into Python using existing tools. If you’re working with spatial data in Python and have waited more than 10 seconds for something to finish, this workshop is for you (and, spoiler alert: you may be waiting too long).

Launched in September 2025, SedonaDB is an analytical database engine built on DataFusion that integrates spatial concepts from its internals (e.g., native data types, joins, and statistics handling) to its interface (e.g., where documentation for hundreds of spatial functions is built in to the interface). SedonaDB offers a cohesive set of principles across Python, R, and SQL designed for compatibility with existing tools (e.g., PostGIS, GeoPandas, GDAL, DuckDB) to facilitate knowledge transfer from both geo-native and database-native users alike.

This workshop is geared towards participants that have familiarity with Python that are interested in learning spatial database and cloud native concepts to work with spatial data that is just a little too big to be comfortable on their laptop. We will cover the building blocks of analytical databases (e.g., tables, joins, scalar functions, and aggregate functions) and how spatial extensions implement them to effectively utilize all of the processors and all of the memory available on your laptop using hands-on examples against real data.

We will use SedonaDB in the workshop as a teaching tool, but will also include a short module ensuring the concepts we apply can be transferred to similar tools such as PostGIS, DuckDB and Apache Sedona for Spark, which all implement a similar mapping of spatial concepts to analytical database implementations.
