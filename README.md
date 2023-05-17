
## JsonFormat

```java
package cn.tanglaoaer.vo;

import com.fasterxml.jackson.annotation.JsonFormat;


/**
 * 用户 类型。
 */
@JsonFormat(shape = JsonFormat.Shape.OBJECT)
public enum UserType {
    ANONYMOUS(-1, "匿名用户"),

    GUEST(0, "B站用户");

    private int value;

    private String label;

    UserType(int value, String label) {
        this.value = value;
        this.label = label;
    }

    public int getValue() {
        return value;
    }

    public void setValue(int value) {
        this.value = value;
    }

    public String getLabel() {
        return label;
    }

    public void setLabel(String label) {
        this.label = label;
    }
}

```

执行EnumToJsonDemo查看结果,这个是加上`@JsonFormat(shape = JsonFormat.Shape.OBJECT)`的时候，枚举值会被当成一个对象显示。
```java
-- before serialization --
MyTestUserType{userType=GUEST, name='hello world'}
-- after serialization --
{"userType":{"value":0,"label":"B站用户"},"name":"hello world"}
```
当不要这个注解的时候、结果是显示这个枚举的名称。
```java
-- before serialization --
MyTestUserType{userType=GUEST, name='hello world'}
-- after serialization --
{"userType":"GUEST","name":"hello world"}
```