FROM ruby
MAINTAINER danny <danny@kray.jp>

ADD http://pkg.jenkins-ci.org/redhat/jenkins.repo /etc/yum.repos.d/jenkins.repo
RUN rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
RUN yum -y install jenkins java-1.7.0-openjdk

RUN mkdir -p /var/lib/jenkins/.ssh
RUN chown -R jenkins:jenkins /var/lib/jenkins/.ssh

# git plugin
ADD http://updates.jenkins-ci.org/latest/git.hpi /var/lib/jenkins/plugins/git.hpi
ADD http://updates.jenkins-ci.org/latest/ssh-credentials.hpi /var/lib/jenkins/plugins/ssh-credentials.hpi
ADD http://updates.jenkins-ci.org/latest/git-client.hpi /var/lib/jenkins/plugins/git-client.hpi
ADD http://updates.jenkins-ci.org/latest/scm-api.hpi /var/lib/jenkins/plugins/scm-api.hpi
ADD http://updates.jenkins-ci.org/latest/ssh-credentials.hpi /var/lib/jenkins/plugins/ssh-credentials.hpi
ADD http://updates.jenkins-ci.org/latest/credentials.hpi /var/lib/jenkins/plugins/credentials.hpi

# hipchat plugin
ADD http://updates.jenkins-ci.org/latest/hipchat.hpi /var/lib/jenkins/plugins/hipchat.hpi

RUN chown -R jenkins:jenkins /var/lib/jenkins/plugins
ADD ./etc/supervisord.d/jenkins.ini /etc/supervisord.d/jenkins.ini

ENV JENKINS_HOME /var/lib/jenkins
