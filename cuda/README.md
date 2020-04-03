g++ add.cpp -o add
nvcc add.cu -o add_cuda -I/usr/local/cuda-9.0/include/ -L/usr/local/cuda-9.0/lib64
nvcc add_block.cu -o add_cuda_blcok -I/usr/local/cuda-9.0/include/ -L/usr/local/cuda-9.0/lib64
nvcc add_grid.cu -o add_cuda_grid -I/usr/local/cuda-9.0/include/ -L/usr/local/cuda-9.0/lib64


sudo /usr/local/cuda/bin/nvprof ./add_cuda 注意用sudo权限

GPU上能跑的函数,在CUDA中称之为kernel.
nvcc可以把cpu代码编译成能在gpu上跑的格式.在函数前指定'__global__'即可.

CUDA kernel launches are specified using the triple angle bracket syntax <<< >>>.

Specifically, threadIdx.x contains the index of the current thread within its block, and blockDim.x contains the number of threads in the block

