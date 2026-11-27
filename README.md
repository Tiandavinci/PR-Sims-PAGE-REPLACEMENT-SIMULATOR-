# PR-Sims: Page Replacement Simulator

A GUI-based (Tkinter) application that simulates the **FIFO**, **LRU**, and **Optimal** page replacement algorithms and shows a step-by-step table of hits and page faults.

## Group Members

| Name | Role |
|------|------|
| Guerra, Kenneth Lawrence | Back-end |
| Oquin, Edmel Cristian | Front-end |
| Matira, Adhyson | |
| Antiniola, Matthew | |
| Corona, Christian Joseph | |
| Martinez, Juan Carlo Gabriel | |

**Course / Section:** BSIT - 2104  **Instructor:** Gerarld James Dano

## Features

- Three algorithms: FIFO, LRU, Optimal
- **Compare All** mode: runs all three on the same input and shows a summary table
- Step-by-step results table (page, frame contents, HIT/FAULT, replaced page)
- Hit ratio and fault ratio per algorithm
- Input validation with error messages

## Requirements

- Python 3.8 or newer
- Tkinter (included with Python on Windows and macOS; on Linux: `sudo apt install python3-tk`)
- No other libraries needed

## How to Run (VS Code)

1. Install **Python 3.8+** (make sure Tkinter is included) and **Visual Studio Code** with the **Python extension**.
2. Download or clone this repository.
3. In VS Code, click **File → Open Folder** and select the project folder.
4. Open page_replacement.py (inside src/).
5. Click the **▶ Run Python File** button at the top right.
6. The "Page Replacement Simulator" window will open.

See the full [User Guide](docs/USER_GUIDE.md).

## Repository Structure

```
├── README.md
├── src/
│   └── page_replacement.py
├── docs/
│   ├── USER_GUIDE.md
│   ├── TESTING.md
│   └── images/            ← screenshots
└── presentation/          ← slides and demo materials
```

## Documentation

- [User Guide](docs/USER_GUIDE.md): execution, inputs, and how to read the output
- [Testing Evidence](docs/TESTING.md): test cases with expected and actual results
- Contribution Record: (paste Google Spreadsheet link here)
- Presentation: see the `presentation/` folder
