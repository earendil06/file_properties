file_properties
=========
[![Build Status](https://travis-ci.com/earendil06/file_properties.svg?branch=master)](https://travis-ci.com/earendil06/file_properties)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-earendil06.file_properties-blue.svg)](https://galaxy.ansible.com/earendil06/file_properties)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/earendil06/file_properties/master/LICENSE)

Role to easily configure a .properties file.

Read more about .properties files : [Properties files](https://en.wikipedia.org/wiki/.properties).

Requirements
------------
* Ansible >= 2.5
* Linux distributions 
    * Ubuntu
        * Trusty (14.04)
        * Xenial (16.04)
        * Bionic (18.04)
        
Role Variables
--------------
The following variables will change the behavior of this role (default values are shown below):

```yaml
#The .properties file to target (mandatory field)
file: file.properties

# Map of pairs to be added
add:
  key1: value1
  key2: value2
  key3: value3
  key4: value4

#List of the keys to be commented
comment:
  - key1
  - key2

#List of the keys to be uncommented
uncomment:
  - key1
  - key2

#List of the keys to be removed
remove:
  - key3
```

Example Playbook
----------------
Minimal playbook:

```yaml
- hosts: localhost
  roles:
    - role: earendil06.file_properties
      file: myFile.properties      
```

Result: nothing has changed, a file is created if not already existing.

Full example:
```yaml
- hosts: localhost
  roles:
    - role: earendil06.file_properties
      file: myFile.properties
      add:
        key1: value1
        key2: value2
        key3: value3
        key4: value4
      comment:
        - key1
        - key2
      uncomment:
        - key2
      remove:
        - key3
```

Result: 

```text
#key1=value1
key2=value2

key4=value4
```

License
-------

MIT

Author Information
------------------
Florent Pastor
