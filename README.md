# Radar Target Generation and Detection Project

## Implementation steps for the 2D CFAR process

First I defined the number of training cells and guard cells along both the doppler and range axes. This was used to create a window with the Cell Under Target (CUT) in the middle, surrounded first by guard cells and then later by target cells.

Then I slid the window one cell at a time through the entire FFT array. At each step, I averaged the signal from all training cells and scaled it by an offset to determine a threshold. If the signal at the CUT was less than the threshold, then I assigned the CUT a value of 0.

## Selection of Training, Guard cells and offset.

For the number of training and guard cells, I used the values initially presented in the Project Overview video. For training cells, I used 10 cells in each direction on the range axis and 8 for the doppler axis while I used 4 guard cells in each direction for both the range and doppler axes. For the offset, I also started with the value given in the video, but this did not remove enough of the noise so I increased it until enough noise was removed, which settled at a value of 10.

## Steps taken to suppress the non-threshold cells at the edges.

To remove cells at the edges, I set to 0 the value of every cell that was never a CUT.
