# User Guide

## 1. Running the Program (VS Code)

1. Install **Python 3.8+** (make sure Tkinter is included) and **Visual Studio Code** with the **Python extension**.
2. Download or clone the repository.
3. In VS Code, click **File → Open Folder** and select the project folder.
4. Open page_replacement.py (inside src/).
5. Click the **▶ Run Python File** button at the top right of the editor.
6. The window "Page Replacement Simulator" opens.

## 2. Screens

The program has three screens: **Title → Input → Results**.

### Title screen
Shows the program name and a short definition of page replacement. Click **START** to continue.

### Input screen
1. **Choose an algorithm** by clicking one of the cards: `FIFO`, `LRU`, `OPTIMAL`, or `COMPARE ALL`. The selected card is highlighted and a short description appears above the input fields.
2. Fill in the two inputs:

| Input | Meaning | Valid values | Example |
|-------|---------|--------------|---------|
| **PAGE FRAMES** | Number of memory frames | Whole number, at least 1 | `3` |
| **PAGE REFERENCE STRING** | Sequence of page requests | Whole numbers separated by spaces (commas also accepted) | `7 0 1 2 0 3 0 4 2 3` |

3. Click **RUN** to simulate, or **BACK** to return to the title screen.

If an input is invalid, an error message appears and nothing runs:
- Frames empty, not a number, or less than 1 → "Number of frames must be a whole number, at least 1."
- Reference string empty or containing non-numbers → "Enter page numbers separated by spaces."

### Results screen
Each algorithm gets its own tab. **COMPARE ALL** adds a **SUMMARY** tab.

## 3. How to Read the Output

### Step table

| Column | Meaning |
|--------|---------|
| Step | Position in the reference string (1, 2, 3, ...) |
| Page | The page requested at that step |
| Frame 1 … Frame N | Pages in memory after that step (`-` means empty) |
| Result | `HIT` (page already in a frame, green) or `FAULT` (page had to be loaded, red) |
| Replaced | The page removed to make room (`-` if a free frame was used or on a hit) |

### Statistics under the table

- **Final Frames**: contents of memory at the end
- **Total Hits / Total Faults**: counts
- **Hit Ratio / Fault Ratio**: percentages out of all references (hits + faults = total references)

### Summary tab (Compare All only)
Lists Hits, Faults, Hit %, and Fault % for FIFO, LRU, and Optimal. The algorithm with the **fewest faults** performs best on that input. Optimal is always the lowest or tied, since it looks ahead at the future references.

## 4. Algorithms in Brief

- **FIFO**: replaces the page that has been in memory the longest.
- **LRU**: replaces the page that was used least recently.
- **Optimal**: replaces the page that will not be used for the longest time in the future.

## 5. Sample Run

Input: Frames = `3`, Reference string = `7 0 1 2 0 3 0 4 2 3 0 3 2 1 2 0 1 7 0 1`

| Algorithm | Hits | Faults |
|-----------|------|--------|
| FIFO | 5 | 15 |
| LRU | 8 | 12 |
| Optimal | 11 | 9 |

<img width="1919" height="1031" alt="Screenshot 2026-11-27 092827" src="https://github.com/user-attachments/assets/04011ffe-2084-4db0-8deb-b28f48d5c648" />
