# herd

  Herd your child processes! A simple wrapper over node cluster for zero-downtime reloads.

## Quickstart

Just pass herd the function to run on the child-processes.

```javascript
var http = require('http');
var herd = require('herd');

herd(function () {
  http.createServer.listen(8000);
});
```

From the terminal, send a `SIGHUP` signal to gracefully reload the process:

```shell
$ kill -1 1922
```

We usually keep the master process really small, and never reload it.

## Options

All of the options are getters (without args) or setters (with args). When you're done, just call `run`.

#### .timeout(ms)

The timeout before killing a worker in ms

#### .boot(ms)

The timeout before considering a worker 'ready'.

#### .handler(fn)

To explicitly set the handler function instead of sending it to `run`

#### .size(workers)

The number of workers. Defaults to the number of cpus.

#### .signal(signal)

The signal to reboot the workers ('SIGHUP')


## License

(The MIT License)

Copyright (c) 2012 Segment.io &lt;friends@segment.io&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
