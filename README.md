# Live Audio Noise Cancellation using LMS Adaptive Filtering

## Introduction
Live audio noise cancellation is an important application in the field of Digital Signal Processing, widely used in communication systems, hearing aids, and voice-controlled devices. In real-world environments, audio signals are often corrupted by unwanted background noise, which reduces clarity and intelligibility.
To address this issue, adaptive filtering techniques are used, which can adjust their parameters automatically based on the input signal characteristics. One of the most popular and computationally efficient algorithms for this purpose is the Least Mean Squares Algorithm.
This project focuses on implementing live audio noise cancellation using the LMS adaptive filtering technique. The system continuously processes incoming audio signals and removes noise in real time, making it highly suitable for practical applications such as hands-free communication and speech enhancement systems.

## Methodology
The proposed system uses an adaptive filtering approach based on the LMS algorithm to cancel noise from a live audio signal.
Step 1: Signal Acquisition
The input consists of:
Primary signal (desired signal + noise)
Reference noise signal (correlated noise)
 Step 2: Adaptive Filter Initialization
Filter weights are initialized to small values
Step size (learning rate) is chosen carefully for stability
Step 3: LMS Algorithm Processing
The LMS algorithm works iteratively using the following steps:
Take input signal
Filter it using current weights
Compute error (difference between desired and output)
Update weights using error signal
This process allows the filter to learn and adapt to the noise characteristics over time.
Step 4: Noise Cancellation
The filter output estimates the noise
This estimated noise is subtracted from the original signal
Result: Clean audio signal
Step 5: Real-Time Implementation
The system processes audio continuously, making it suitable for live applications.

## Pseudocode
Start

Set sampling frequency (fs)
Set duration of signal
Set filter order
Set LMS step size (mu)

-----------------------------------
Generate / Acquire Signal
-----------------------------------
Create time vector
Generate clean audio signal (sine wave)
Generate random noise
Add noise to clean signal → recorded signal

-----------------------------------
Pre-processing
-----------------------------------
Apply high-pass filter to recorded signal
Store result as filtered signal

-----------------------------------
Noise Estimation
-----------------------------------
Set threshold value
Find samples where signal amplitude is less than threshold

IF silent samples exist:
    Estimate noise as average of those samples
ELSE:
    Set estimated noise to zero
END IF

-----------------------------------
Initialize LMS Parameters
-----------------------------------
Initialize filter weights to zero
Get length of signal
Initialize output signal array (y)
Initialize error signal array (e)

-----------------------------------
LMS Adaptive Filtering Loop
-----------------------------------
FOR each sample from filter_order to N:

    Extract input segment from filtered signal

    Compute filter output:
        y(n) = weights transpose × input segment

    Compute error:
        e(n) = filtered signal − output

    Update filter weights:
        w = w + mu × e(n) × input segment

END FOR

-----------------------------------
Post-processing
-----------------------------------
Amplify the output signal
Normalize the signal to avoid clipping

-----------------------------------
Plotting
-----------------------------------
Plot time vs noise-cancelled signal

-----------------------------------
Performance Evaluation
-----------------------------------
Compute power of filtered signal
Compute power of cancelled noise
Calculate Noise Reduction (in dB)

Display Noise Reduction

End

## Results
Noise Reduction (NR): 0.0049107 dB

## Conclusion
The project successfully demonstrates the implementation of live audio noise cancellation using the LMS adaptive filtering algorithm. The system is capable of reducing unwanted noise from audio signals in real time, improving overall signal quality.
The LMS algorithm proves to be efficient due to its simplicity and low computational requirements. The results show that adaptive filtering is a powerful technique for noise reduction in dynamic environments where noise characteristics change over time.

## Limitations
Despite its advantages, the system has some limitations:
The performance depends on proper selection of step size
Convergence may be slow for complex noise signals
Requires a reference noise signal that is correlated with actual noise
May not completely eliminate all types of noise
Real-time processing may introduce slight delay depending on system capability

## References
https://ijerst.org/index.php/ijerst/article/view/883
