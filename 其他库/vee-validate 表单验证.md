---
title: vee-validate 表单验证
date: 2023-01-14T22:51:37Z
lastmod: 2023-01-14T22:55:59Z
---

# vee-validate 表单验证

使用步骤

* 使用第三包提供的`Form`​标签将表单整个区域包裹起来, 如果要进行整体验证, 需要给`Form`​打`ref`​
* 使用第三方包提供的`Filed`​标签将输入框的`input`​替换掉
* 如果表单需要校验，那么必须有`name`​属性
* 将校验规则通过`rules`​绑定到需要校验的`Field`​标签上
* 当用户输入的内容未通过验证规则时，错误信息是从`Form`​标签上的插槽中解构出来的

引入组件

```ts
    import { Form, Field } from "vee-validate";
```

‍

模板写法

```ts
                        <Form
                            v-slot="{ errors }"
                            ref="fromValidate"
                        >
                            <div class="input-text clearFix">
                                <span></span>
                                <Field
                                    type="text"
                                    placeholder="邮箱/用户名/手机号"
                                    v-model="phone"
                                    name="account"
                                    :rules="checkAccount"
                                />
                                <h1 style="color: red">{{ errors.account }}</h1>
                            </div>
                            <div class="input-text clearFix">
                                <span class="pwd"></span>
                                <Field
                                    type="text"
                                    placeholder="请输入密码"
                                    v-model="password"
                                    name="password"
                                    :rules="checkPassword"
                                />
                                <h1 style="color: red">
                                    {{ errors.password }}
                                </h1>
                            </div>
                            <button
                                class="btn"
                                @click.prevent="login"
                            >
                                登&nbsp;&nbsp;录
                            </button>
                        </Form>
```

书写验证规则

```ts
    // 定义验证规则
    const checkAccount = (val: unknown) => {
        const reg = /^[\a-zA-Z0-9_]+$/;
        if (!val) {
            return "请输入账号";
        } else {
            if (reg.test(val as string)) {
                return true;
            } else {
                return "账号不合法 请输入6-16位数字字母下划线";
            }
        }
    };
    const checkPassword = (val: unknown) => {
        if (!val) {
            return "请输入密码";
        } else {
            return true;
        }
    };
```

进行整体验证

```ts
    const login = async () => {
            const { valid } = await fromValidate.value?.validate();
            console.log(valid);

            if (valid) {
                // 如果验证通过进行下一步
                ...
            }
    };
```
