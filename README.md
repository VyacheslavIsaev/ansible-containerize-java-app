Containerize JAVA app
=========

Role allows to containerize an arbitrarry JAVA application on a remote host.

Requirements
------------

Docker installed on the remote host.

Role Variables
--------------

* app_name - application name
* app_ports [] - array of application ports to expose
* app_maintainer - maintainer string
* app_image_name - app image name. Default: "{{app_name}}:latest"
* docker_file - local path to docker file
* app_path    - path to install sources on the remote host
* app_build_cmd  Default: "mvn clean install"
* app_srcs [] - Array of sources


Example Playbook
----------------

    - hosts: all
      roles:
        - role: "vyacheslavisaev.containerize_java_app"
          vars:
            app_name:  "java-server"
            app_port: "8888"
            app_ports: [
              "{{app_port}}"
            ]
            app_maintainer: "v.isaev@email.com"
            app_src: ["./src", "pom.xml"]
            docker_file: "docker/.Dockerfile.singlestage"

License
-------

BSD

Author Information
------------------

Viacheslav Isaev has two decades of experience of distributed high payload systems development. He has been in charge of developing control systems for safety-critical facilities like railroads and particle accelerators, high-payload event processing systems for cybersecurity and mobile access points, introducing in house CI/CD practices. His hands-on experience incldues all stages of IT solutions development and operation. Vyacheslav’s interests lays in automation spectr either it is pure software or hardware-software solutions. Vyacheslav defines the key to success in 3 pillars  Domain Driven Design, Behavioral Driven and Test-Driven Development, which are standing on the foundation of  Object Oriented Design and Clean Code practices.