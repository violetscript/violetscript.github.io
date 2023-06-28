# Adobe AIR

Once the VioletScript compiler is done, there may be support for converting VioletScript bytecode into AVM2 bytecode, allowing to create apps with the [Adobe AIR framework](https://airsdk.harman.com) maintained by Samsung HARMAN.

## File system

```
import com.adobe.air.filesystem.*;

use resource (fileStream = new FileStream()) {
    fileStream.open(new File(import.meta.url).resolvePath('../output.txt'));
    fileStream.writeUTFBytes('Output!');
}
```