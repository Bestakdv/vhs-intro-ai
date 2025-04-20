### Model casting
1. What does the `print_param_dtype()` function do?
Prints out the data types of the parameters in a model
2. Show the code that can be used to **cast** the model parameters to bfloat16 data
type.
.to(torch.bfloat16)
3. What do we mean by performing an **inference** of a model.
An inference is when a model makes a prediction on new and unseen data.
4. What is `deepcopy` used in this video?
Makes a copy of the model so that it can be modified without changing the original model
5. The `model_bf16` uses lesser precision than the FP32 `model`. In the video, how
do they compare the impact of this low precision on the model performance? Is the
performance degradation significant?
They compare the 2 models responses to the image of a woman with a dog. It is not significant and didn't really impact the overall
performance of the model
### Loading model in low precision
6. Name the Pytorch method that can be used to get the memory footprint of a model.
.get_memory_footprint()
7. How is loading the model at low precision better than downcasting the weights of
a loaded model?
It is better to load a model as it is more memory efficient and has a faster loading time.
### Linear quantisation
8. How is linear quantisation different from lower precision floating point
representation?
Linear quantization maps a range of higher precision values to smaller range values whereas lower precision floating point uses a
floating point data type that has fewer bits to represent the number.
10. How does linear quantization lead to lower memory footprint?
It convers floating-point values to lower-precision integers leading to a reduction in data per parameters.
