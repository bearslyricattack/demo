```
////建立数据库连接，数据库名：数据库密码
//dsn := "root:123456@tcp(127.0.0.1:3306)/dbgotest"
//db, err := gorm.Open(mysql.Open(dsn), &gorm.Config{})
////处理错误
//if err != nil {
// //控制台打印错误日志
// panic("数据库连接失败!")
//}
////新建数据库表，根据结构体创建
//m := db.Migrator()
//err = m.CreateTable(&User{})
//if err != nil {
// panic("新建表失败!")
//}
////配置http
//h := server.Default(
// server.WithHostPorts("127.0.0.1:8080"),
//)
//h.GET("/hello", func(c context.Context, ctx *app.RequestContext) {
// //获取参数
// username := ctx.Query("name")
// //创建一条数据，传入一个对象
// db.Create(&User{Name: username})
// //查询一条数据
// var user User
// db.First(&user, "name = ?", username)
// //转换格式后输出
// res, _ := json.Marshal(user)
// ctx.String(consts.StatusOK, string(res))
//})
```

```
// User 定义gorm model5个用法
type User struct {
   Name string `gorm:"column:name; type:varchar(32);"`
}

// TableName 定义表名
func (U User) TableName() string {
   return "User"
}
```

```
"github.com/cloudwego/hertz/pkg/app"
"github.com/cloudwego/hertz/pkg/app/server"
"github.com/cloudwego/hertz/pkg/common/json"
"github.com/cloudwego/hertz/pkg/protocol/consts"
"gorm.io/driver/mysql"
"gorm.io/gorm"
```