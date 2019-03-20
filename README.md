# Ansible Role: SSL Deploy

## Requirements

This role should run any linux host, debian or redhat variant.

## Role Variables
	dest_crt_path: "/etc/pki/tls/certs/"
	dest_key_path: "/etc/pki/tls/private/"
	dest_crt_name: "generic-cert.crt"
	dest_key_name: "generic-key.key"
	src_crt_template_path: "/path/to/generic-cert.crt"
	src_key_template_path: "/path/to/generic-key.key"
	src_key_var: !vault |
	src_crt_var: !vault |


## Example Playbooks

### Deploy with certificate + key in files:
	  roles:
	    - role: ssldeploy
		    dest_crt_path: "/etc/pki/tls/certs/"
		    dest_key_path: "/etc/pki/tls/private/"
		    dest_crt_name: "generic-cert.crt"
		    dest_key_name: "generic-key.key"
		    src_crt_template_path: "/path/to/generic-cert.crt"
		    src_key_template_path: "/path/to/generic-key.key"

### Deploy with certificate + key as variable:
	  roles:
	    - role: ssldeploy
		    dest_crt_path: "/etc/pki/tls/certs/"
		    dest_key_path: "/etc/pki/tls/private/"
		    dest_crt_name: "generic-cert.crt"
		    dest_key_name: "generic-key.key"
	      # Generated encrypted var string by ansible-vault encrypt_string --prompt
		    src_key_var: !vault |
			$ANSIBLE_VAUL;1.1;AES256
			...
			...
		    src_crt_var: !vault |
			$ANSIBLE_VAUL;1.1;AES256
			...
			...
