# live-component-application

1. 应用方式 gradle
```
implementation 'com.jrhlive:component.screensize:1.0.1'
```
2.自定义使用方式
在component-screen-size中的build.gradle文件中，自己修改task可以按照自己的需要来生成dimens文件，
```
/**
 * 生成values.xml
 */
task createDp(group: "jrh") {
    def path = project.getRootDir().path
    def file = new File("$path/component-screen-size/src/main/res/values/dimens.xml")
    def range = 0..800
    file.withWriter('UTF-8') { writer ->
        writer.write("""<?xml version="1.0" encoding="utf-8"?>
<resources>\n""")
        range.each { dimen ->
            writer.write("""    <dimen name="dx_dp_${dimen}">${dimen}dp</dimen>\n""")
            writer.write("""    <dimen name="dx_dp_${dimen}_5">${dimen}.5dp</dimen>\n""")
        }
        writer.write("""</resources>\n""")
    }
}

```

3.项目右键，菜单栏找到screen-match,使用screen-match生成新的dimens文件

