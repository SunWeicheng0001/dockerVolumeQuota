#####2015/8/13
1. 修改daemon/container_unix.go 增加 GetVolumesSize() 返回map[string]int64, 增加MonitorVolumeSize\n
2. 修改daemon/volumes_unix.go 中register()中registerMountPoints(container *Container, hostConfig *runconfig.HostConfig)增加代码，每20秒自动执行MonitorVolumesSize

#####2015/8/14
1. 修改opts/opts.go中 validatePath(val string, validateMountMode bool) (string, error)中case 2部分，使之能够支持逗号分隔的volume commlandLine部分的解析
