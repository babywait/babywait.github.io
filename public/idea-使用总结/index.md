# IDEA 使用总结


## 设置

### 内存设置：编码丝滑不卡顿

作用：解决 IDEA 编辑、多开项目等卡顿的问题，让编码更丝滑

配置方式：有很多种途径，这里只写一种，`Help -> Edit Custom VM Options`

配置项：

```shell
-Xms1024m #最小启动内存参数
-Xmx8192m #最大运行内存参数
-XX:ReservedCodeCacheSize=512m #保留代码占用的内存容量参数
```

### 内存显示：看见心里踏实

{{< figure src="images/image-20240627231408629.png">}}

### 自动 import & 清除无用 import

{{< figure src="images/image-20240627232954318.png">}}

### 禁用 import *

{{< figure src="images/image-20240627233157994.png">}}

### 代码提示忽略大小写

{{< figure src="images/image-20240627234343555.png">}}



### live template

#### nl

```java
List<$var$> $end$ = new ArrayList<>();
```

{{< figure src="images/image-20240627233903424.png">}}

#### np

```java
Map<$val1$, $val2$> $val3$ = new HashMap<>();
```



### File and Code Templates 

#### Enum

```java
#parse("Copyright.java")
#if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end
import com.fasterxml.jackson.annotation.JsonCreator;
import com.fasterxml.jackson.annotation.JsonValue;

import java.util.Optional;

#parse("Author.java")
public enum ${NAME} {

    ;
    
    private int value;
    
    private String name;
    
    ${NAME}(int value, String name) {
        this.value = value;
        this.name = name;
    }

    public static Optional<${NAME}> findByInt(int value) {
        for (${NAME} item: ${NAME}.values()) {
            if (item.value == value) {
                return Optional.of(item);
            }
        }
        
        return Optional.empty();
    }

    public static Optional<${NAME}> findByString(String name) {
      for (${NAME} item: ${NAME}.values()) {
            if (item.name.equals(name)) {
                return Optional.of(item);
            }
        }
        
        return Optional.empty();
    }
    
    @JsonCreator
    public static ${NAME} findNullableByString(String name) {
      for (${NAME} item: ${NAME}.values()) {
            if (item.name.equals(name)) {
                return item;
            }
        }
        
        return null;
    }

    @JsonValue
    public String toString() {
        return this.name;
    }
    
    public int toInt() {
        return this.value;
    }
}
```



## 快捷键设置

### 打开最近的项目：option + R

{{< figure src="images/image-20240627235156879.png">}}

### 打开：option + O

{{< figure src="images/image-20240627234944484.png">}}



## 常用内置快捷键

### 重构代码

|   快捷键   |                          作用                          |
| :--------: | :----------------------------------------------------: |
| Shift + F6 |             Rename（包、类、方法、变量等）             |
| ⌘ + ⌃ + G  | Select All Occurrences（选中并编辑所有当前单词的地方） |
| ⌘ + ⌥ + M  |                将选中代码抽取成 Method                 |
| ⌘ + ⌥ + C  |               将选中代码抽取成 Constant                |
| ⌘ + ⌥ + V  |               将选中代码抽取成 Variable                |
| ⌘ + ⌥ + F  |                 将选中代码抽取成 Field                 |
| ⌘ + ⌥ + P  |               将选中代码抽取成 Parameter               |
| ⌘ + ⌥ + T  |  将选中代码 Surround With if/try catch/Runnable.....   |



## Debug tips

[IDEA中如何使用debug调试项目 一步一步详细教程](https://blog.csdn.net/yxl_1207/article/details/80973622)



## IDEA 插件

### Maven Helper：pom 可视化&依赖冲突排包

{{< figure src="images/image-20240628084836293.png">}}

### MultiHighlight：高亮选中变量

快捷键：`⌘ + "` 和 `⌘ + Shift + "`

{{< figure src="images/image-20240628002451595.png">}}

### Translation：翻译

快捷键：`⌘ + ⌃ + I` 和 `⌘ + ⌃ + U`

{{< figure src="images/image-20240628003132131.png">}}



### String Manipulation：字符串

{{< figure src="images/image-20240628085114391.png">}}

### Key Promoter X：快捷键提示

{{< figure src="images/image-20240628085238617.png">}}



### Lombok：自动生成 getter/setter

### GitToolBox

### GsonFormatPlus

### PlantUML integration

### SequenceDiagram：生成代码调用时序图

{{< figure src="images/image-20240628085828427.png">}}

## 参考资料

[IntelliJ IDEA神器使用技巧](https://www.bilibili.com/video/BV1Ft411V7rf/?p=6&vd_source=96daa63dca9ca2bbc59250a649e16c49)

[IDEA 官方文档](https://www.jetbrains.com/help/idea/getting-started.html)

