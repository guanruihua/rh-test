# 描述

- 更名为 **unit-test-js**
- 添加测试用例来执行是否符合预期

## `test<Param, Tobe>(name:string, func:Func, ...cases: CaseUnit<Param, Tobe>)`

- 泛型
  - `Param` : 测试用例的参数类型
  - `Tobe`: 测试用例的结果类型
- 参数
  - `name`: 用例名
  - `func`: 待测试的方法
  - `...cases`: 测试用例

```ts

export type CaseUnit<Param, Tobe> = {
 func?: any
 name?: string
 param?: Param
 params?: Param | Param[]
 tobe?: _Tobe<Tobe>
 tobes?: _Tobe<Tobe>[]
 warningTobe?: _Tobe<Tobe>
 warningTobes?: _Tobe<Tobe>[]
 type?: CaseUnitType
 paramType?: CaseUnitParamType
 /**
  * 测试执行前
  */
 before?: callback<Param, Tobe>
 /**
  * 判断结果是否正确前
  */
 beforeEqual?: callback<Param, Tobe>
 /**
  * 打印结果前
  */
 after?: callback<Param, Tobe>
 /**
  * @title 超时时间
  * @default 2000
  */
 timeout?: number | 'Infinite'
 run?: {
  actual: any,
  runTime: number,
  error?: string
 }
 [key: string]: any
}

test(name, func, {...},{...}, ...)
// 可以打印出相应的结果
```

## `equal<Param, Tobe>`

- 等同 `test(name, tobe, ...)`
- 方法的参数加了默认值
