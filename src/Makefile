libs=-I../../scheduling/lib -I/usr/lib/jvm/java-1.8.0-openjdk-amd64/include -I/usr/lib/jvm/java-1.8.0-openjdk-amd64/include/linux
#caching global memory
#caching=-Xptxas -dlcm=ca
params=-std=c++11 --expt-extended-lambda -lcuda
gen=-gencode arch=compute_20,code=sm_20 -gencode arch=compute_30,code=sm_30 -gencode arch=compute_35,code=sm_35 -gencode arch=compute_37,code=sm_37 -gencode arch=compute_50,code=sm_50 -gencode arch=compute_52,code=sm_52 -gencode arch=compute_60,code=sm_60 -gencode arch=compute_61,code=sm_61

#first=MinSortExample
first=MinSortCloudSim

all: minsort cost

minsort: MinSortCloudSim.cu
	nvcc $(gen) $(libs) -o libMinSortCloudSim.so -shared -Xcompiler -fPIC MinSortCloudSim.cu $(params) -DELAPSED_TIME=$(TIME)

cost: CloudSimCost.cu
	nvcc $(gen) $(libs) -o libCloudSimCost.so -shared -Xcompiler -fPIC CloudSimCost.cu $(params) -DELAPSED_TIME=$(TIME)





