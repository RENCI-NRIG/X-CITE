# Python exercise for CHESS users

## Step 1: Logging in
Following the [Linux exercises for CHESS users](https://github.com/RENCI-NRIG/X-CITE/blob/main/theme2/SF100/exercises.md):
1. Open a terminal on `lnx201`
1. Change directory to your CHESS user directory

## Step 2: Create input files
Open a file editor and create the following three files (file.txt, file.data, and file.json) by copying and pasting the contents below for each file:
```
# file.txt (file with a text)
Hello world!!!

# file.data (file with numeric array)
[1,2,3,4,5]

# file.json (file with json data)
{"int": 1, "array": [1,2,3], "dictionary": {"key":"value"}}
```
## Step 3: Interact with files
The following code will walk you through the following steps:
- how to open a file in python
- how to read data from a file
  - become familiar with different data structures: string, array, dictionary, etc.
- how to manipulate the data (e.g. perform some analysis)
  - how to mix different data structures together
- how to write data to a file

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

## Setting up python virtual environment
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

## How to Deactivate the Virtual Environment

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

