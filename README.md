# node-profiling

Simple profiling in a NodeJS application, leveraging **--prof --prof-process and Apache Bench**

* Installs and runs the application
`npm install`
` NODE_ENV=production node --prof app.js` and
* Creates an user and puts some load on the server using Apache Bench
```
curl -X GET "http://localhost:3000/newUser?username=william&password=123"
ab -k -c 78 -n 300 "http://localhost:3000/auth?username=william&password=123"
```

* Generates the profiling and save in processed.txt
```
node --prof-process isolate-0x102884000-13773-v8.log > processed.txt
```
* If you analyze the benchmark, you can easily identify that crypto is causing the bottleneck. Thankfully, we can generate the hash asynchronously and the difference it perceptive. Left side is using synchronous, whereas the right side is using asynchronous call.

![](https://raw.githubusercontent.com/iwilliam317/node-profiling/master/benchmark.png)



*Please note that these are NOT recommended handlers for authenticating users in your Node.js applications and are used purely for illustration purposes. You should not be trying to design your own cryptographic authentication mechanisms in general. It is much better to use existing, proven authentication solutions.*
