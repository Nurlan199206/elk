# elk
ELK - Active Directory integration


ELK: ```8.4.3```


```systemctl start kibana```


```systemctl start elasticsearch```


```/usr/share/elasticsearch/bin/elasticsearch-reset-password -u kibana_system```


```/usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic```


```systemctl restart kibana```


```systemctl restart elasticsearch```



```/usr/share/elasticsearch/bin/elasticsearch-keystore add  \
xpack.security.authc.realms.active_directory.my_ad.secure_bind_password
```


```
PUT /_security/role_mapping/admins
{
  "roles" : [ "monitoring" , "user" ],
  "rules" : { "field" : {
    "groups" : "CN=grafana-admins,CN=Users,DC=nurlan,DC=kz" 
  } },
  "enabled": true
}
```


```
PUT /_security/role_mapping/basic_users
{
  "roles" : [ "user" ],
  "rules" : { "any": [
    { "field" : {
      "groups" : "CN=grafana-editors,CN=Users,DC=nurlan,DC=kz" 
    } },
    { "field" : {
      "dn" : "CN=grafana-editors,CN=Users,DC=nurlan,DC=kz" 
    } }
  ] },
  "enabled": true
}
```

![image](https://github.com/Nurlan199206/elk/assets/22808731/f00e7056-c761-47da-ab0c-e4e68455c6df)
