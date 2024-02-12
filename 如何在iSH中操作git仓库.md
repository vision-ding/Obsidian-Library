##### clone仓库到iSH
1. `cd ~ && mkdir obsidian -- 在home目录下，新建obsidian目录`
2. `mount -t ios . obsidian --挂载 obsidian app 的文件存储目录到刚才创建的 obsidian 目录`
3. 删除vault中的.obsidian目录
4. 切到obsidian目录
5. `git clone "repo ssh" vault`