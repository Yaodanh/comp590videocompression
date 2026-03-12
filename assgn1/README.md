# Assignment 1: Lossless Video Compression Challenge

## Implementation Overview
In this assignment, I implemented a lossless video compression system using context-adaptive arithmetic coding. By leveraging spatial correlations within each video frame, the compressor achieves significant data reduction while maintaining bit-perfect reconstruction.

### Key Features:
- 256 Arithmetic Coding Contexts: Instead of a single probability model, I utilized 256 independent ‘VectorCountSymbolModel’ instances.
- Spatial Context Selection: The context for each pixel is determined by the value of the pixel immediately to its left in the current frame ($ContextID = Pixel_{left}$).
- Boundary Handling: For the first pixel in each row, a default context value of ‘128’ is applied.
- Residual Encoding: The system calculates the difference between the current frame and the prior frame, ensuring a 100% lossless reconstruction.

## Experimental Results
The implementation was evaluated using the ‘bourne.mp4’ dataset with the following results:

| Metric | Value |
| :--- | :--- |
| Frames Processed | 10 |
| Average Frame Size | 5,900,156 bits |
| Compression Ratio | 2.81 |
| Verification | Passed (‘correct.’ via ‘-check_decode’) |

## How to Run
To verify the results and check for correctness:
```bash
cargo run --release -- -count 10 -check_decode
