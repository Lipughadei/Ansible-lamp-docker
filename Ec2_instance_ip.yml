---
- name: Create an EC2 instance
  hosts: localhost
  gather_facts: no
  tasks:
    - name: Launch EC2 instance
      ec2:
        key_name: jenkins1
        instance_type: t2.micro
        image: ami-0e0e417dfa2028266
        region: ap-south-1
        wait: yes
        count: 1
        vpc_subnet_id: subnet-00d4449399bba6d92
        assign_public_ip: yes
        group: Hello
      register: ec2

    - name: Output instance details
      debug:
        var: ec2

    - name: Retrieve EC2 instance facts
      ec2_instance_facts:
        region: ap-south-1
        filters:
          instance-state-name: running
      register: ec2_facts

    - name: Output EC2 facts
      debug:
        var: ec2_facts

    - name: Check if any instances are found
      debug:
        msg: "No running instances found."
      when: ec2_facts.instances | length == 0

    - name: Display instance IP addresses
      debug:
        msg: "Instance ID: {{ item.instance_id }}, Public IP: {{ item.public_ip | default('N/A') }}, Private IP: {{ item.private_ip | default('N/A') }}"
      loop: "{{ ec2_facts.instances }}"
      when: ec2_facts.instances | length > 0
