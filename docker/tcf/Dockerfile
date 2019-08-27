FROM sammyne/hyperledger-tcf-vm:alpha 

LABEL maintainer=lixiangmin01@baidu.com

RUN apt update -y && apt install -y vim
RUN cd /project && rm -rf TrustedComputeFramework &&\
   git clone --branch play --depth 1 https://github.com/sammyne/trusted-compute-framework.git &&\
   mv trusted-compute-framework TrustedComputeFramework &&\
   cd /project/TrustedComputeFramework/tools/build &&\
   echo "CLEAN BUILD..." && make clean && echo "DONE CLEAN" && make && echo "BUILD SUCCESS"

WORKDIR /project/TrustedComputeFramework