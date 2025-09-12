---
title: building sg3_utils for windows
---


## why
should you need any of the code changes done after release 1.48

## where
* https://github.com/doug-gilbert/sg3_utils

## needed
* opensuse tumbleweed (can be wsl2 version)
* mingw cross compilation stuff

## packages
```
% zypper se -is mingw
Loading repository data...
Reading installed packages...

S  | Name                         | Type    | Version      | Arch   | Repository
---+------------------------------+---------+--------------+--------+-----------
i  | mingw64-cross-binutils       | package | 2.42-1.4     | x86_64 | repo-oss
i  | mingw64-cross-binutils-utils | package | 2.42-1.4     | x86_64 | repo-oss
i+ | mingw64-cross-cmake          | package | 1.1.5-1.10   | noarch | repo-oss
i  | mingw64-cross-cpp            | package | 13.2.0-3.5   | x86_64 | repo-oss
i+ | mingw64-cross-filesystem     | package | 20250422-1.1 | noarch | mingw64
i+ | mingw64-cross-gcc            | package | 13.2.0-3.5   | x86_64 | repo-oss
i  | mingw64-cross-pkgconf        | package | 1.6.3-5.8    | x86_64 | repo-oss
i  | mingw64-filesystem           | package | 20250901-1.1 | noarch | repo-oss
i  | mingw64-headers              | package | 12.0.0-1.2   | noarch | repo-oss
i  | mingw64-libwinpthread1       | package | 12.0.0-1.2   | noarch | repo-oss
i+ | mingw64-pkgconf              | package | 1.6.3-5.8    | noarch | repo-oss
i  | mingw64-runtime              | package | 12.0.0-1.2   | noarch | repo-oss
i+ | mingw64-winpthreads-devel    | package | 12.0.0-1.2   | noarch | repo-oss


% zypper lr mingw64
Alias          : mingw64
Name           : mingw64
URI            : https://download.opensuse.org/repositories/windows:/mingw:/win64/openSUSE_Tumbleweed
Enabled        : Yes
GPG Check      : (r ) Yes
Priority       : 99 (default priority)
Autorefresh    : On
Keep Packages  : Off
Type           : rpm-md
GPG Key URI    :
Path Prefix    :
Parent Service :
Keywords       : ---
Repo Info Path : /etc/zypp/repos.d/mingw64.repo
MD Cache Path  : /var/cache/zypp/raw/mingw64


% zypper lr repo-oss
Alias          : openSUSE:repo-oss
Name           : repo-oss
URI            : http://cdn.opensuse.org/tumbleweed/repo/oss
Enabled        : Yes
GPG Check      : (r ) Yes
Priority       : 99 (default priority)
Autorefresh    : On
Keep Packages  : Off
Type           : rpm-md
GPG Key URI    : http://cdn.opensuse.org/tumbleweed/repo/oss/repodata/repomd.xml.key
Path Prefix    :
Parent Service : openSUSE
Keywords       : [5]
    gpg-pubkey-09d9ea69-67c857f3.asc?fpr=1C59D66FCD52563A16933DBCFEC28EAF09D9EA69
    gpg-pubkey-29b700a4-62b07e22.asc?fpr=AD485664E901B867051AB15F35A2F86E29B700A4
    gpg-pubkey-39db7c82-66c5d91a.asc?fpr=FEAB502539D846DB2C0961CA70AF9E8139DB7C82
    gpg-pubkey-3fa1d6ce-67c856ee.asc?fpr=7F009157B127B994D5CFBE76F74F09BC3FA1D6CE
    pool
Repo Info Path : /etc/zypp/repos.d/openSUSE:repo-oss.repo
MD Cache Path  : /var/cache/zypp/raw/openSUSE:repo-oss

```

## process
```
git clone https://github.com/doug-gilbert/sg3_utils.git
cd sg3_utils
./bootstrap
./configure --host=x86_64-w64-mingw32 --enable-win32-spt-direct  --enable-static --enable-shared=no
make
find . -iname '*exe'

```
## check
sg_inq version should be reported as 2.58, last official release reports 2.48:

```
sg_inq.exe -V
Version string: 2.58 20231213

sg_inq.exe -V
Version string: 2.48 20230606

```

