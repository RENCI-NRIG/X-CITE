# Python Exercises for CHESS Users
Wherever you see `<your CLASSE username>` below, substitute your own CLASSE username.

## Exercise 1: Log in and navigate to CHESS user directory
Following the [Linux exercises for CHESS users](https://github.com/RENCI-NRIG/X-CITE/blob/main/theme4/XS101/linux-exercises.md):
1. Open a terminal on `lnx201`
1. Change directory to your CHESS user directory: `cd /nfs/chess/user/<your CLASSE username>`

## Exercise 2: Create input files
In your CHESS user directory, type following command to copy three files (file.txt, file.data, and file.json) to your current directory (`.`):
```
cp /nfs/chess/user/x-cite/data/python/* .
```
[Optional] Instead of copying the above files, type the following commands to create your own from scratch:
```
# file.txt (file with a text)
echo 'Hello world!' > file.txt

# file.data (file with numeric array)
echo '[1,2,3,4,5]' > file.data

# file.json (file with json data)
echo '{"int": 1, "array": [1,2,3], "dictionary": {"key":"value"}}' > file.json
```

Now, view and check the contents of each file using `cat`, `less`, or `more`.

## Exercise 3: Interact with files
This exercise demonstrates some of the basic steps of any data analysis: reading data, processing or interacting with data, writing data. These steps can be iterated any number of times and combined in many ways.

Note the conceptual similarity between these data analysis pipelines and the [Linux pipes demonstrated in the Linux exercises](https://github.com/RENCI-NRIG/X-CITE/blob/main/theme4/XS101/linux-exercises.md) (taking one command output and pass it to another, e.g. env | grep USER`).

The following code will walk you through the following steps:
- how to open a file in python
- how to read data from a file
  - become familiar with different data structures: string, array, dictionary, etc.
- how to manipulate the data (e.g. perform some analysis)
  - how to mix different data structures together
- how to write data to a file

Let's proceed with basic analysis using python:
1. Type `python` (in the same directory where the files you created above are located). This will open an interactive python session.
1. Type the commands below and observe the output:
```
# open file
open('file.txt')

# open file and assign it to a file descriptor
fds = open('file.txt')

# read data from our file descriptor
data = fds.read()
print("text data:", data)

# close the file descriptor
fds.close()

# load data from a data file
data = open('file.data', 'r').read()
print("structural data:", data)

# load json data from a json data file
import json
data = json.load(open('file.json', 'r'))
print("json data:", data)

# let's perform data analysis on our data and enhance it further
if 'array' in data:
    arr = data['array']
    for item in arr:
        print("array item", item)
    data['sum'] = sum(arr)

# let's create our own data and write it back to new file
with open('analysis.json', 'w') as ostream:
    ostream.write(json.dumps(data))
```
3. Type `Ctrl-D` to exit the interactive python session

## Exercise 4: Set up Python virtual environment
A **virtual environment** is a self-contained directory that contains a Python installation
for a particular project, along with all its packages. It isolates project dependencies,
ensuring that different projects don't interfere with each other's libraries and versions.

**Why use it?**
- Avoid dependency conflicts between projects.
- Safely test upgrades without affecting system Python.
- Clean, reproducible development environments.

---

#### How to Set Up and Activate a Virtual Environment

1. **Install `virtualenv` (optional)**
Python 3.x comes with `venv` built-in command which we can use to create and setup virtual environment
```
python3 -m venv myenv
```
- `myenv` is the name of the folder where the environment will be created.

2. **Activate the Virtual Environment**

- **On Linux/macOS**:
  ```bash
  source myenv/bin/activate
  ```

- **On Windows (cmd.exe)**:
  ```cmd
  myenv\Scripts\activate
  ```

- **On Windows (PowerShell)**:
  ```powershell
  .\myenv\Scripts\Activate.ps1
  ```

Once activated, your shell prompt will change to show the environment name, e.g., `(myenv)`.

---

#### How to Install a Package Inside the Virtual Environment

While the virtual environment is **activated**, you can install packages normally using `pip`:

```bash
pip install requests
```

- Example: Installing a specific version:
  ```bash
  pip install requests==2.28.1
  ```

All installed packages will now live inside the `myenv` directory.

---

#### How to Deactivate the Virtual Environment

When you're done working inside the virtual environment, simply run:

```bash
deactivate
```

This will return you to the original system Python environment.

---

#### Quick Summary
| Action        | Command                                  |
|---------------|------------------------------------------|
| Create venv   | `python3 -m venv myenv`                  |
| Activate venv | `source myenv/bin/activate` (Linux/macOS)|
| Install pkg   | `pip install <package>`                 |
| Deactivate    | `deactivate`                             |

