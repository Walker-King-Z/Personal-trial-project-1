# Walker-King-Z/Personal-trial-project-1

一个网易云音乐自动打卡刷每日推荐歌曲及歌单云函数

## 关于

- 本项目fork自 李小控LittleControl
- 本项目后端基于[NeteaseCloudMusicApi](https://github.com/Binaryify/NeteaseCloudMusicApi)
- 由于Vercel免费额度问题,先已不再提供搭建好的后端API,还请自行搭建,搭建步骤还请参考[NeteaseCloudMusicApi在 vercel 上的部署](https://neteasecloudmusicapi.vercel.app/#/?id=vercel-%e9%83%a8%e7%bd%b2),当然也不必非局限于Vercel这个平台

## 已实现的功能

- [x] 自动打卡签到,包括 PC 端(网页端)和安卓端,以及云贝签到
- [x] 自动刷歌,每日推荐歌曲以及每日推荐歌单里面的歌曲
- [x] 多国手机号登陆支持
- [x] 适配相关云平台日志输出,其实就是加了一些`console.log`并`try-catch`了一下
- [x] 多账号功能支持


## 使用方法

1. 下载 release 页面压缩包,或者`clone`代码,自己安装 npm 依赖
2. 登陆云平台,(腾讯云,阿里云等),进入云函数页面,并新建一个云函数
3. 函数环境选择 nodejs 的最新版本,函数入口填`index.main`,内存选择`128MB`,超时时间填入`100`即可
4. 然后将代码上传到平台,修改`config/account`,第一行为自己的网易云绑定的手机号,第二行为对应的明文密码,如果手机号为国内号码,则直接填入号码即可,不需要加区域码,但如果是国外手机号,则必须加区域码,比如美国手机号`+1xxxxxxx`.如果有多个账号,则按照格式,比如第一行为账号,第二行为密码,第三行为账号,第四行为密码,以此类推
5. (可选操作),修改`config/api`文件内容为自己的 API 地址,默认我已经搭好的地址,建议使用自己的 API 地址,具体搭建参考[NeteaseCloudMusicApi](https://neteasecloudmusicapi.vercel.app/#/?id=vercel-%e9%83%a8%e7%bd%b2)在 vercel 上的部署
6. 部署函数并测试,查看日志定位原因
7. 设置触发器,触发器就是根据你设定的条件自动执行函数,选择时间触发器,然后你可以根据提示设置,好像有的是要填 cron 表达式啥的,比如` 0 0 4 * * *`,这个就是北京时间每天`12:00`执行,具体的可以自己研究一下表达式该怎么写
8. 保存,并开始摸鱼
