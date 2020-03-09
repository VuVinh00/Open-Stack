# Backup and SnapShots
## 1. Backup
**Step:1 Tạo 1 Volume sau đó gắn Volume vào VM đang chạy:**
```sh
$ openstack volume create volume-1 --size 10
$ openstack server add volume server-1 volume-1
```
**Step 2: Trên máy VM thực hiện `mount` sau đó ghi dữ liệu vào volume mới attach
```sh
$ touch test01.txt
$ touch test02.txt
```
**Step 3: `umount` sau đó `detach` `volume-1`
**Step 4: Thực hiện Backup volume**
```sh
$ openstack volume backup create --name backup-1 volume-1
```
**Step 5: Tạo 1 volume mới và restore bản `backup-1` vào volume này:**
```sh
$ openstack volume create volume-2 --size 10
$ openstack volume backup restore backup-1 volume-2
```
**Step 6: Gắn `volume-2` vào VM, thực hiện `mount` sau đó kiểm tra:**
```sh
$ openstack server add volume server-1 volume-2
```

## 2. SnapShots


- http://training.nectar.org.au/package10/sections/managingVolumes.html
- http://training.nectar.org.au/package09//sections/backup.html