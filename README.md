#####2015/8/13
1. 修改daemon/container_unix.go 增加 GetVolumesSize() 返回map[string]int64, 增加MonitorVolumeSize\n
2. 修改daemon/volumes_unix.go 中register()中registerMountPoints(container *Container, hostConfig *runconfig.HostConfig)增加代码，每20秒自动执行MonitorVolumesSize

#####2015/8/14
1. 修改opts/opts.go中 validatePath(val string, validateMountMode bool) (string, error)中case 2部分，使之能够支持逗号分隔的volume commlandLine部分的解析
2. 修改runconfig/hostconfig.go 中的HostConfig，增加BindsQuota
3. 修改runconfig/parse.go中关于解析的部分
4. 修改daemon/Volumes.go中mountPoint，增加Size
5. 修改daemon/volume_unix.go, 使之可以根据命令行初始化mountPoint中Size部分

####2015/8/15
1. 修改runconfig/parse.go，fix了加入逗号会出现两个挂载点的漏洞
2. 修改daemon/volume_unix.go，放弃了原来采用的已经再到废弃的container.Volumes，换成了container.MountPoints
3. 修改daemon/volume_unix.go，修改了MonitorVolumesSize()，使到达一定大小时会发出警告，退出container时会退出这个线程

####2015/8/17
1. 修改runconfig/parse.go opts/opts.go 将逗号改成了问号，并且支持GB/gb/KB/kb/MB/mb的输入
