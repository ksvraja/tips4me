# Keep the build files in temp folder

### Create RAM file system
[reference](https://wiki.archlinux.org/title/tmpfs)

```
/etc/fstab

tmpfs   /build         tmpfs   rw,nodev,nosuid,size=2G          0  0
```

### Configure gradle
Configure gradle to use the /build directory for all build outputs.

~/.gradle/init.gradle

```
gradle.projectsLoaded {
    rootProject.allprojects {
        buildDir = "/build/${rootProject.name}/${project.name}"
    }
}
```
