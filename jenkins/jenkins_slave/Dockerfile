FROM openshift/jenkins-slave-base-centos7:v3.11

MAINTAINER Nicolas Masse <nmasse@redhat.com>

# Labels consumed by Red Hat build service
LABEL name="openshift3/jenkins-agent-ansible-26-rhel7" \
      version="3.11" \
      architecture="x86_64" \
      io.k8s.display-name="Jenkins Agent Ansible" \
      io.k8s.description="The jenkins agent ansible image has the Ansible engine on top of the jenkins slave base image." \
      io.openshift.tags="openshift,jenkins,agent,ansible"

USER root
RUN yum install -y ansible && \
    yum install -y python27-python-pip && \
    scl enable python27 "pip install --install-option='--install-purelib=/usr/lib/python2.7/site-packages/' jinja2" && \
    yum clean all && \
    rm -rf /var/cache/yum && \
    chown -R 1001:0 $HOME && \
    chmod -R g+rw $HOME

USER 1001
