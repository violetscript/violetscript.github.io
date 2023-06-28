# Embed Expression

The context keyword `embed` can be used to include text or octet-stream of relative path to the current script.

```
var ba:ByteArray = embed './octetStream.bin';
var str:String = embed './someText.txt';
```