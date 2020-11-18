# 关于git的日常使用

## 打patch：
1. 生成patch  
	1.生成最近一次提交的patch： git format-patch HEAD^
2. 检测是否能够打上patch
	1. git apply --check 0001...		没有输出，即能正常打上
3. 打patch 
	1. git am 0001...
