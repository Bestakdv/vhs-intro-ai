# Quantization Fundamentals with Hugging Face (Deeplearning.ai course)
Ref: https://learn.deeplearning.ai/courses/quantization-fundamentals
## Lesson 1: Introduction
Watch `Introduction`, and then answer these questions:
1. Andrew mentions **PyTorch** library. What is PyTorch? Which library that you
have used so far in the course is similar to PyTorch?
PyTorch is a library that allows for machine learning and is used for training neural networks.
A library similar to PyTorch is Keras.
3. Andrew also talks about **data types**. What are data types used for? List the
data types that are mentioned in this video.
Data types are used to define a variable and how it can be stored.The datatypes mentioned in the video are float and integers.
4. What is the purpose of this course?
Pros and cons of each data type, how to load models with different data types and linear quantization.
Watch `Handling Big Models`, and then answer these questions:
5. Why is handling big models a problem for the AI community?
Not everybody has the devices to run AI, so big models arent accessible to everyone.
6. To solve this problem, the video mentions 2 techniques (not covered in detail)
apart from quantization. What are they?
Pruning: removing layers that are not that important in the models decision
Knowledge Distillation: Training a smaller model (student) using the original model (instructor) and transfering the knowledge
7. What makes a model "big"? Should we be concerned about where we store the model
or how we run the model? Or both?
The parameters make a model "big" and we should be concerned where the model is stored as it could be too big to run because of too many
bytes.
8. The video describes how quantization is done by moving from floating point
(FP32) to integer (INT8). Explain how this makes the model "smaller".
It makes the model smaller as in FP32 it needs 4 bytes to store each value while in INT8 it only needs 1 byte,
however it can cause quantization error.
## Lesson 2: Data types & sizes
Watch `Data types & sizes` video to answer the questions below:
### Integer data type
The video shows the range of values for the 2 types of integer data types:
**unsigned integer** and **signed integer**.
8. Show the formula used to calculate the **range**.
The formula for the unsigned integer range is [0,2^n -1]
The formula for signed integer range is [-2^(n-1), 2^(n-1) - 1]
9. Compute the range for **unsigned int** with 8-bits. Show the steps in your
calculation.
Minimum: 0+0+0+0+0+0+0+0 = 0
Maximum: 2^7 + 2^6 +2^5 + 2^4 + 2^3 + 2^2 + 2^1 + 2^0 = 255
[0,255]
10. Compute the range for **signed int** with 8-bits. Show the steps in your
calculation.
Maximum: 0*2^7 + 1*2^6 + 1*2^5 + 1*2^4 + 1*2^3 + 1*2^2 + 1*2^1 + 1*2^0 = 127
Minimum: -1(0*2^7 + 1*2^6 + 1*2^5 + 1*2^4 + 1*2^3 + 1*2^2 + 1*2^1 + 1*2^0 + 1) = -128
[-128,127]
11. Represent the values, 2, 6, 33 and 100 in the 8-bit unsigned int data format.
2: 00000010
6: 00000110
33: 00100011
100: 01100100
12. What is the value represented by **11010101** in unisgned integer format? What
is the value in signed integer format?
2^7 + 2^6 + 0 +2^4 + 0 + 2^2 + 0 + 2^0= 213
### Floating point data type
13. What type of data is stored using the floating point data type?
Numbers with decimals
14. Explain the 3 components in the floating point data type. Identify the
components that represent the **range** and **precision**.
The 3 components are sign, exponent(range), and fraction(precision)
16. What is "floating" in this data type? Explain with an example.
It refers to how the decimal point can move an example being 5000 as 5*10^3.
17. Compare FP32, FP16 and BF16 formats in terms of precision and range.
FP32: Range 8 bits, precision 23 bits (best)
BF16: Range 8 bits, precision 7 bits (better)
FP16: Range 5 bits, precision 10 bits (good)
19. The video mentions **tensor**. What is a tensor?
A tensor holds elements of single data types and it is the main way to store data in PyTorch
20. What PyTorch function can I use to print the range of the floating point data
type? Show the code for checking the range for the brain float BF16 data type.
print(torch.finfo(torch.bfloat16))
### Impact of downcasting
20. What is **downcasting**? Why do it?
Downcasting is when a higher data type is converted to a lower data type (an example being float to integer) to
reduce memory footprint.
22. What is the impact of **downcasting** on the result of matrix multiplication?
The values get increased/changed after downcasting
23. Why did the video choose matrix multiplication to check the impact of
downcasting on the precision of the result?
The video choose matrix multiplication as its easy to compare and it shows the rounding errors.
24. One of the advantages of downcasting is reduced memory footprint. How does this
allow us to enable larger batch sizes? Why is having larger batch sizes beneficial
to training?
It allows to train larger batch sizes by reducing the reducing the memory so there is more space to train batch sizes
and it beneficial because it makes training faster
26. The video mentions a use case of **mixed precision training** with downcasting.
Why would this work?
This would work as it would apply lower precision where it improves efficiency and keeping the others in high precision.
