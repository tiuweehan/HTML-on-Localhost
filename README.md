# Serve HTML to Localhost

Do you have a HTML file that you want to serve to localhost, but don't want to create a separate file like app.js to serve it? If you have nodejs installed, fret not! Here are a few simple steps to make your life easier.

1. Plop the following alias into bash_profile or bashrc

```
alias servehtml='function _serve { echo "const http = require('\'http\''); const fs = require('\'fs\''); const hostname = '\'127.0.0.1\''; const port = '\'\$2\''; fs.readFile('\'\$1\'', function (err, html) { if (err) { throw err; } const server = http.createServer(function(request, response) { response.writeHeader(200, {\"Content-Type\": \"text/html\"}); response.write(html); response.end(); }).listen(port, hostname, () => { console.log(\`Server running at http://\${hostname}:\${port}/\`); }); });" | node; unset _serve; }; _serve' 
```

2. Source bash_profile / bashrc depending on which file you inserted the alias into

3. Run servehtml \<html file to be served\> \<port on localhost\>. For example, running the following command will display the html file 'index.html' on port 3000

```
servehtml index.html 3000
```
