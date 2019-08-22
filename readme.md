### Compile single module
javac -d out/client.module src/client.module/module-info.java src/client.module/com/esempla/client/Main.java

### Run application containing single module
java --module-path out --module client.module/com.esempla.client.Main
java -p out -m client.module/com.esempla.client.Main

### Packaging
jar -cfe mods/client.module.jar com.esempla.client.Main -C out/client.module .

### Run module
java --module-path mods --module client.module
java -p mods -m client.module
java --show-module-resolution --limit-modules java.base -p mods -m client.module

### Linking modules
jlink --module-path mods/;$JAVA_HOME/jmods --add-modules client.module --output client-image

### Running application with the Generated Image
cd client-image\bin
java --module client.module/com.esempla.client.Main

### Linking modules with launcher script
jlink --module-path mods/;$JAVA_HOME/jmods --add-modules client.module --launcher client-launcher=client.module --output client-image

### Run launcher script
client-image\bin\client-launcher














