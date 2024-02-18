# simple pipeline as code using a java application

assuming that the application in java does something and we are devopsing it without knowing what it does

## Getting Started

start 3 instances on the cloud or install vagrant/virtualbox locally.. to prevent any cost i decided to run it locally

### Prerequisites

You'll need the following installed on your machine:

- vagrant
- virtualbox
  if running in the cloud you just need an aws account

### Installation

Follow these steps to get the pipeline environment running:

1. Clone the repository:

   ```bash
   git clone https://github.com/AnassBenzanzoun/pipeline-as-code-vagrant-vms.git
   ```

2. Navigate to the project directory:

   ```bash
   cd pipeline-as-code-vagrant-vms
   ```

3. start the vms:

   ```bash
   vagrant up
   ```

   this will get the images from vagrantCloud automatically and install it
   then it will automatically run the bash files inside the repo for each server individually

   wait for it to boot up then ssh inside each vm for more configurations
   each service have it's own setup website in which it's running:

   - jenkins run by default on port 8080
   - sonar qube runs on port 9000
   - nexus run on port 8081

4. Make sure every service can comunicate with the other.. if using ec2 instances you must configure
   each security group properly by using their private ip addresses:

5. since jenkins is the main guy here make sure it has all the plugins it needs to setup the integrations wih the other services:

### plugins

- Nexus artifact uploader -> this allow you to upload the artifact to nexus if everything goes well
- Sonar qube scanner -> this allow sonar qube to integrate with jenkins and gives back reports based on our code analysis

- build timestamp -> this allow us to get the current timestamp to use it as name in the artifact for versioning

- pipeline maven integration -> this allow us to integrate with maven since we are using java
- pipeline utility steps -> this allow us to deploy all the steps for our pipeline as code

## Usage

    you can either trigger the pipeline by running it manually or by adding webhooks to your project
    to configure Webhooks in GitHub:

    In your GitHub repository, go to Settings > Webhooks > Add webhook.
    Set the Payload URL to http://your-jenkins-server/github-webhook/.
    Set the Content type to application/json.
    Select individual events or choose to send everything.
    Configure Jenkins Job:

    In your Jenkins job configuration, go to the "Build Triggers" section.
    Check the option "GitHub hook trigger for GITScm polling."

    you must also use webhooks in sonar qube if your code quality gates are different from the
    default
