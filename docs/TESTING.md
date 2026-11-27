# Testing Evidence

**Program:** Page Replacement Simulator
**Tested on:** (Windows 11, Python 3.12)
**Testers:** (OQUIN, EDMEL CRISTIAN / ANTIONIOLA MATTHEW)

Expected values were worked out by hand and from the standard textbook examples, then compared with the program's actual output.

## A. Algorithm Test Cases

### Test Case 1: Standard reference string, 3 frames
**Input:** Frames = `3`, Refs = `7 0 1 2 0 3 0 4 2 3 0 3 2 1 2 0 1 7 0 1`

| Algorithm | Expected Faults | Actual Faults | Expected Hits | Actual Hits | Result |
|-----------|----|----|----|----|--------|
| FIFO | 15 | 15 | 5 | 5 | Pass |
| LRU | 12 | 12 | 8 | 8 | Pass |
| Optimal | 9 | 9 | 11 | 11 | Pass |

**Screenshot:**

<img width="1919" height="1029" alt="Screenshot 2026-11-27 093627" src="https://github.com/user-attachments/assets/3f36d61c-b576-4522-b1b8-cfba5b86da2e" />



### Test Case 2: Short string, 3 frames
**Input:** Frames = `3`, Refs = `7 0 1 2 0 3 0 4 2 3`

| Algorithm | Expected Faults | Actual Faults | Expected Hits | Actual Hits | Result |
|-----------|----|----|----|----|--------|
| FIFO | 9 | 9 | 1 | 1 | Pass |
| LRU | 8 | 8 | 2 | 2 | Pass |
| Optimal | 6 | 6 | 4 | 4 | Pass |

FIFO hand trace (final frames `4 2 3`):

| Step | Page | Frames | Result |
|------|------|--------|--------|
| 1 | 7 | 7 - - | FAULT |
| 2 | 0 | 7 0 - | FAULT |
| 3 | 1 | 7 0 1 | FAULT |
| 4 | 2 | 2 0 1 | FAULT (replaced 7) |
| 5 | 0 | 2 0 1 | HIT |
| 6 | 3 | 2 3 1 | FAULT (replaced 0) |
| 7 | 0 | 2 3 0 | FAULT (replaced 1) |
| 8 | 4 | 4 3 0 | FAULT (replaced 2) |
| 9 | 2 | 4 2 0 | FAULT (replaced 3) |
| 10 | 3 | 4 2 3 | FAULT (replaced 0) |

**Screenshot:**

<img width="1919" height="1030" alt="Screenshot 2026-11-27 093956" src="https://github.com/user-attachments/assets/d8163ccf-2447-4399-b530-628a6c9d1212" />



### Test Case 3: Belady's anomaly (FIFO gets worse with more frames)
**Input:** Refs = `1 2 3 4 1 2 5 1 2 3 4 5`

| Frames | Algorithm | Expected Faults | Actual Faults | Result |
|--------|-----------|----|----|--------|
| 3 | FIFO | 9 | 9 | Pass |
| 4 | FIFO | 10 | 10 | Pass |
| 3 | LRU | 10 | 10 | Pass |
| 4 | LRU | 8 | 8 | Pass |
| 3 | Optimal | 7 | 7 | Pass |
| 4 | Optimal | 6 | 6 | Pass |

**Screenshot:**

<img width="1919" height="1030" alt="Screenshot 2026-11-27 094320" src="https://github.com/user-attachments/assets/096a8b6a-f1b2-4710-ab2d-7990e4338ffa" />

<img width="1919" height="1033" alt="Screenshot 2026-11-27 094357" src="https://github.com/user-attachments/assets/1928941c-b793-4fb5-9314-f2bada13f1dc" />



### Test Case 4: Same page repeated (edge case)
**Input:** Frames = `2`, Refs = `1 1 1 1`

| Algorithm | Expected | Actual | Result |
|-----------|----------|--------|--------|
| FIFO / LRU / Optimal | 1 fault, 3 hits, final frames `1 -` | 1 fault, 3 hits, final frames `1 -` | Pass |

**Screenshot:**

<img width="1919" height="1034" alt="Screenshot 2026-11-27 094836" src="https://github.com/user-attachments/assets/fc25402b-2d49-4c11-a103-e4f858eb92c2" />



## B. Input Validation Test Cases

| # | Frames | Reference String | Expected | Actual | Result |
|---|--------|------------------|----------|--------|--------|
| 5 | `0` | `1 2 3` | Error popup: frames must be a whole number, at least 1 |
| 6 | `abc` | `1 2 3` | Same error popup |
| 7 | `3` | `1 a 3` | Error popup: enter page numbers separated by spaces |
| 8 | `3` | (empty) | Same error popup |
