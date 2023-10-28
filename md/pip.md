# PIP #


#  #更新命令

    python.exe -m pip install --upgrade pip
##使用说明
## Commands: ##


|名称|介绍|中文|
|:---|:---|:---
|install| Install packages|安装包|
|download|Download packages|下载包|
|uninstall|Uninstall packages|卸载包|
|freeze|Output installed packages in requirements format|以需求格式输出已安装的包|
|inspect|Inspect the python environment| 检查 python 环境|
|list| List installed packages|列出已安装的包|
|show|Show information about installed packages|显示有关已安装软件包的信息|
|check|Verify installed packages have compatible dependencies|检查验证已安装的包是否具有兼容的依赖项|
|config|Manage local and global configuration|管理本地和全局配置|
|search| Search PyPI for packages|在PyPI中搜索程序包|
|cache|Inspect and manage pip's wheel cache|检查和管理pip的车轮缓存|
|index|Inspect information available from package indexes|检查程序包索引中的可用信息|
| wheel| Build wheels from your requirements|根据您的需求打造车轮|
|hash|Compute hashes of package archives|计算包存档的哈希|
|completion|A helper command used for command completion|用于完成命令的助手命令|
|debug| Show information useful for debugging.|显示对调试有用的信息。|
|help|Show help for commands|显示命令的帮助|
## General Options: ##
|名称|介绍|中文|
|:---|:---|:---|
|  -h, --help|Show help|显示帮助|
|  --debug|Let unhandled exceptions propagate outside the main subroutine, instead of logging them to stderr|让未处理的异常在主子程序之外传播，而不是将它们记录到stderr|
| --isolated|Run pip in an isolated mode, ignoring environment variables and user configuration|在隔离模式下运行pip，忽略环境变量和用户配置|
| --require-virtualenv| Allow pip to only run in a virtual environment; exit with an error otherwise.|允许pip只在虚拟环境中运行；否则将退出并返回错误。|
|--python <python>|Run pip with the specified Python interpreter.|允许pip只在虚拟环境中运行；否则将退出并返回错误。|
|-v, --verbose|Give more output. Option is additive, and can be used up to 3 times|提供更多输出。选项为添加选项，最多可使用3次|
|-V, --version|how version and exit.|如何版本和退出。|
|-q, --quiet|Give less output. Option is additive, and can be used up to 3 times (corresponding to WARNING, ERROR, and CRITICAL logging levels)|输出更少。选项是可添加的，最多可使用3次（对应于WARNING、ERROR和CRITICAL日志记录级别）|
|--log <path>|Path to a verbose appending log.|详细附加日志的路径。|
|--no-input|Disable prompting for input.|禁用输入提示。|
|--proxy <proxy>|Specify a proxy in the form scheme://[user:passwd@]proxy.server:port|以scheme://[user:passwd@]proxy.server:port的形式指定代理|
|--retries <retries>|Maximum number of retries each connection should attempt (default 5 times)|每个连接应尝试的最大重试次数（默认为5次）|
|--timeout <sec>|Set the socket timeout (default 15 seconds)|设置套接字超时（默认为15秒）|
|--exists-action <action>|Default action when a path already exists: (s)witch, (i)gnore, (w)ipe, (b)ackup,(a)bort|路径已存在时的默认操作：（s）witch，（i）gnore，（w）ipe，（b）ackup，（a）bort|
|--trusted-host <hostname>|Mark this host or host:port pair as trusted, even though it does not have valid or any HTTPS.|将此主机或host:port对标记为受信任，即使它没有有效的HTTPS或任何HTTPS。|
| --cert<path>|Path to PEM-encoded CA certificate bundle. If provided, overrides the default. See 'SSL Certificate Verification' in pip documentation for more information|将此主机或host:port对标记为受信任，即使它没有有效的HTTPS或任何HTTPS。|
|--client-cert <path>|Path to SSL client certificate, a single file containing the private key and the certificate in PEM format|SSL客户端证书的路径，包含私钥和PEM格式证书的单个文件|
|--cache-dir <dir>|Store the cache data in <dir>|将缓存数据存储在＜dir＞中
|--no-cache-dir|Disable the cache.|禁用缓存。|
|--disable-pip-version-check|Don't periodically check PyPI to determine whether a new version of pip is available for download. Implied with --no-index.|不要定期检查PyPI来确定是否有新版本的pip可供下载。隐含--无索引。|
|--no-color|Suppress colored output|抑制彩色输出|
|--no-python-version-warning|Silence deprecation warnings for upcoming unsupported Pythons.2|对即将推出的不受支持的Python发出静音弃用警告。2|
|--use-feature <feature>|Enable new functionality, that may be backward incompatible.|启用可能向后不兼容的新功能。|
|--use-deprecated <feature>| Enable deprecated functionality, that will be removed in the future.|启用不推荐使用的功能，这些功能将来将被删除。

