FROM jenkins/jenkins:2.249.2
COPY plugins_extra.txt /usr/share/jenkins/ref/plugins_extra.txt
COPY /casc_configs /var/jenkins_conf
LABEL maintainer="ignas.liudavicius@gmail.com"

ENV JENKINS_HOME /var/jenkins_home

# Add support for proxies.
# Values should be passed as build args
# http://docs.docker.com/engine/reference/builder/#arg
ENV http_proxy ${http_proxy:-}
ENV https_proxy ${https_proxy:-}
ENV no_proxy ${no_proxy:-}
ARG JAVA_PROXY
ENV JAVA_PROXY ${JAVA_PROXY:-}
ARG JAVA_OPTS

ENV JAVA_OPTS "-Djenkins.CLI.disabled=true -Djenkins.install.runSetupWizard=false ${JAVA_PROXY:-} -Dorg.apache.commons.jelly.tags.fmt.timeZone=Europe/Stockholm ${JAVA_PROXY:-}"

RUN jenkins-plugin-cli -f /usr/share/jenkins/ref/plugins_extra.txt
