Student ReadMe file for Project Rubric:

Implementation steps for 2D CFAR:
Given the number of training and guard cells, we loop through
the sliding window of training+guard+CUT cells.
For each window, calculate estimated noise level in the 
training cells. The average noise levels together with 
the constant threshold gives the threshold for this window.
Check if CUT level exceeds threshold. If exceeds, CUT is a 
signal.
As we slide over range-doppler map, the threshold is adaptively 
changed to keep FAR constant.
Once we go through entire Range-Doppler map, I used matlab's 
logical indexing to set any unthresholded cells to zero.

Selection of Training and Guard Cells
I started out with small number of training and guard cells. 
Guard cell for range = 4 and doppler = 2 seems to be safe
considering we dont have much traffic in the scenario.
However, I had to increase the number of training cells since
we only have one target in the scenario. I had many false signals with small number of training cells. Also code would run slower.

Selection of SNR Offset
Finally I increase the constant SNR offset until all false alarms are removed and only the signal around actual target 
remains. Looking at the range doppler map yiels range around 110m and velocity around -20m/s. 
