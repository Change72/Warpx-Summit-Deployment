# Warpx-Summit-Deployment

I followed the instruction [Warpx Summit](https://warpx.readthedocs.io/en/latest/install/hpc/summit.html#id1)

source $HOME/summit_warpx.profile

bash $HOME/src/warpx/Tools/machines/summit-olcf/install_gpu_dependencies.sh
source /ccs/proj/$proj/${USER}/sw/summit/gpu/venvs/warpx-summit/bin/activate


cd $HOME/src/warpx
rm -rf build_summit

cmake -S . -B build_summit -DWarpX_COMPUTE=CUDA -DWarpX_PSATD=ON -DWarpX_QED_TABLE_GEN=ON -DWarpX_DIMS="1;2;RZ;3"
cmake --build build_summit -j 8

Then I try 'bsub summit_v100.bsub' and get the error.

As for the input file, I have tested it on our own server and it can generate a small dataset smoothly.


**Update: Even I try to only use CPU (see the last line of bsub), I still get the same error.**
