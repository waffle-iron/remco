---
date: 2016-10-05T17:24:57+02:00
title: Sample configuration file
---


```
#remco.toml
################################################################
# Global configuration
################################################################
log_level = "debug"
log_format = "text"


################################################################
# Resource configuration
################################################################
[[resource]]
  [[resource.template]]
    src = "/etc/confd/templates/test.cfg"
    dst = "/home/rkaufmann/haproxy.cfg"
    checkCmd = ""
    reloadCmd = ""
    mode = "0644"

  [resource.backend]
    [resource.backend.etcd]
      nodes = ["127.0.0.1:2379"]
      client_cert = "/path/to/client_cert"
      client_key = "/path/to/client_key"
      client_ca_keys = "/path/to/client_ca_keys"
      username = "admin"
      password = "p@SsWord"
      version = 3

      # These values are valid in every backend
      watch = true
      prefix = "/"
      onetime = true
      interval = 1
      keys = ["/"]

    [resource.backend.file]
      filepath = "/etc/remco/test.yml"

    [resource.backend.consul]
      nodes = ["127.0.0.1:8500"]
      scheme = "http" #{http/https}
      client_cert = "/path/to/client_cert"
      client_key = "/path/to/client_key"
      client_ca_keys = "/path/to/client_ca_keys"
    
    [resource.backend.vault]
      node = "http://127.0.0.1:8200"
      ## Token based auth backend
      auth_type = "token"
      auth_token = "vault_token"
      ## AppID based auth backend
      # auth_type = "app-id"
      # app_id = "vault_app_id"
      # user_id = "vault_user_id"
      ## userpass based auth backend
      # auth_type = "userpass"
      # username = "username"
      # password = "password"
      client_cert = "/path/to/client_cert"
      client_key = "/path/to/client_key"
      client_ca_keys = "/path/to/client_ca_keys"

```      