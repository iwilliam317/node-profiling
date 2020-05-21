# node-profiling

Please note that these are NOT recommended handlers for authenticating users in your Node.js applications and are used purely for illustration purposes. You should not be trying to design your own cryptographic authentication mechanisms in general. It is much better to use existing, proven authentication solutions.

* Create an user and puts some load on the server using ApacheBench
```
curl -X GET "http://localhost:3000/newUser?username=william&password=123"
ab -k -c 20 -n 250 "http://localhost:3000/auth?username=william&password=123"
```

* Generates the profiling and save in processed.txt
```
node --prof-process isolate-0x102884000-13773-v8.log > processed.txt
```
