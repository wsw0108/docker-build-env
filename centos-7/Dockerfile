FROM nimmis/java-centos:openjdk-8-jdk

ARG user=wsw

LABEL "maintainer"="wsw0108@qq.com"

# RUN curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo

RUN yum update -y && \
yum install -y which less file && \
yum install -y make && \
yum install -y gcc gcc-c++ && \
yum install -y libstdc++-static libstdc++-static.i686 && \
yum install -y glibc-devel.i686 libstdc++-devel.i686 && \
yum install -y maven && \
yum install -y golang && \
# yum install -y epel-release && \
# yum install -y nodejs && \
yum install -y centos-release-scl-rh && \
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-SIG-SCLo && \
yum install -y rh-nodejs8 && \
echo "source scl_source enable rh-nodejs8" > /etc/profile.d/enable-rh-nodejs8.sh && \
yum install -y http://opensource.wandisco.com/centos/7/git/x86_64/wandisco-git-release-7-2.noarch.rpm && \
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-WANdisco && \
yum install -y git && \
yum install -y cairo cairo-devel libjpeg-turbo-devel pango pango-devel giflib-devel && \
yum clean all

# install yarn & node-gyp
RUN PATH=/opt/rh/rh-nodejs8/root/usr/bin:$PATH npm install -g yarn
RUN PATH=/opt/rh/rh-nodejs8/root/usr/bin:$PATH yarn global add node-gyp

USER $user

# RUN git config --global credential.helper 'cache --timeout 3600'
RUN git config --global credential.helper 'store'
# RUN npm config set registry https://registry.npm.taobao.org/

# Set environment variables.
ENV HOME /home/$user

# Define working directory.
WORKDIR $HOME/projects

VOLUME ["$HOME/projects", "$HOME/.m2", "$HOME/.npm"]

# Define default command.
CMD ["bash"]
