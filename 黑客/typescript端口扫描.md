python版本
```python
import socket


def retBanner(ip, port):
    try:
        socket.setdefaulttimeout(2)
        s = socket.socket()
        s.connect((ip, port))
        banner = s.recv(1024)
        return banner
    except:
        return


def main():
    ip1 = "192.168.95.148"
    ip2 = "192.168.95.149"
    port = 21
    banner1 = retBanner(ip1, port)
    banner2 = retBanner(ip2, port)
    if banner1:
        print '[+]' + ip1 + ':' + banner1
    if banner2:
        print '[+]' + ip2 + ':' + banner2


if __name__ == '__main__':
    main()

```

index.ts
```typescript
function scan(host, start, end, callback) {
    var net = require('net');
    var count = end - start;
    var result = [];
    console.time('port scan time');

    for (var i = start; i <= end; i++) {
        var item = net.connect({
            host: host,
            port: i
        },
            function (i) {
                return function () {
                    result.push(i);
                    this.destroy();
                };
            }(i)
        );

        item.on('error', function (err) {
            if (err.errno == 'ECONNREFUSED') {
                this.destroy();
            }
        });

        item.on('close', function () {
            if (!count--) {
                console.timeEnd('port scan time');
                callback(result);
            }
        });
    }
}

scan('127.0.0.1', 1, 65535, function (result) {
    for (var i = 0; i < result.length; i++) {
        console.log('端口:' + result[i]);
    }
});
```

shadow.ts
```typescript
import net = require('net');

export namespace Shadow {
    export class Socket {
        connect(host, port) {
            return new Promise((resolve, rejecct) => {
                var client = net.connect(port, host, (s) => {
                    // console.log('连接上了' + client.bytesRead + client.bytesWritten);
                    client.write('hello \n');
                });
                client.setTimeout(2, () => {
                    // console.log('延时')
                    client.destroy();
                    resolve();
                });



                client.on('end', (err) => {
                    // console.log('没有链接成功')
                });


                client.on('data', (data) => {
                    var result = data.toString();
                    console.log('接收数据:' + result);
                    resolve(result);
                    client.end();
                });

            });
        }
    }
}
```