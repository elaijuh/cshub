# Abstract

To understand OCI(Open Container Initiative) runtime-spec and image-spec

# Prerequisites

runc, containerd, nerdctl

# runtime-spec

[OCI runtime-spec][oci-runtime-spec] defines detailed APIs for runtime developers to follow.

- `ociVersion`

- `id`

- `status`

- `pid`

- `bundle`

- `annotation`

## runc

[runc][runc] is a implementation of OCI runtime-spec, it spawns and runs containers on Linux. runc is based off libcontainer.

### Generate runc spec with bundle

Bundle nginx image to a .tar file under rootfs/

```sh
$ nerdctl images

REPOSITORY    TAG       IMAGE ID        CREATED       PLATFORM       SIZE       BLOB SIZE
nginx         alpine    c04c18adc2a4    4 days ago    linux/amd64    47.63MB    18.59MB

$ mkdir rootfs
$ nerdctl save c04c18 -o rootfs/nginx.tar

$ tar -tf rootfs/nginx.tar

blobs/
blobs/sha256/
blobs/sha256/0c57fe90551cfd8b7d4d05763c5018607b296cb01f7e0ff44b7d047353ed8cc0
blobs/sha256/0f0eda053dc5c4c8240f11542cb4d200db6a11d476a4189b1eb0a3afa5684a9a
blobs/sha256/35b039ba2bc54667ad0fdce04367ea93ed097b0506cda323e280e1ed31f29b31
blobs/sha256/41c49cbde6a69c2861d4443a90e47a59e906386088b706d32aba1091d0f262b0
blobs/sha256/45f552c78c312f2b711135f5af71a2eb06e223246d13cae7bf3a15e447136045
blobs/sha256/532b9a30583c1bf82204f3cbc8054882bace1669cc85fdcb45b8f88b4db82833
blobs/sha256/62a896bb4a21c26afb24814d77cc345822fd8b03255bb9f940a0707daa9f2ff6
blobs/sha256/7f5898476db744b7e3d5f25c7533b4285e21cf2025610f339cb32bf39bebcfe4
blobs/sha256/9da224fdd4124c20879a425f59ee3d7e9aeccf37356692f37cd7736e38c2efd2
blobs/sha256/c04c18adc2a407740a397c8407c011fc6c90026a9b65cceddef7ae5484360158
blobs/sha256/c6a83fedfae6ed8a4f5f7cbb6a7b6f1c1ec3d86fea8cb9e5ba2e5e6673fde9f6
index.json
manifest.json
oci-layout

```

Generate runc spec

```

```

# image-spec

Inspect image to get information

Id:
RepoDigest:
Architecture
Os
RootFS

```sh
$ nerdctl images nginx

REPOSITORY    TAG       IMAGE ID        CREATED         PLATFORM       SIZE       BLOB SIZE
nginx         alpine    c04c18adc2a4    25 hours ago    linux/amd64    47.63MB    18.59MB

$ nerdctl image inspect c04c18

[
    {
        "Id": "sha256:0f0eda053dc5c4c8240f11542cb4d200db6a11d476a4189b1eb0a3afa5684a9a",
        "RepoTags": [
            "nginx:alpine"
        ],
        "RepoDigests": [
            "nginx@sha256:c04c18adc2a407740a397c8407c011fc6c90026a9b65cceddef7ae5484360158"
        ],
        "Parent": "",
        "Comment": "buildkit.dockerfile.v0",
        "Created": "2024-08-14T23:51:24Z",
        "DockerVersion": "",
        "Author": "",
        "Config": {
            "AttachStdin": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.27.1",
                "PKG_RELEASE=1",
                "DYNPKG_RELEASE=2",
                "NJS_VERSION=0.8.5",
                "NJS_RELEASE=1"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "Labels": {
                "maintainer": "NGINX Docker Maintainers \u003cdocker-maint@nginx.com\u003e"
            }
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 47632384,
        "VirtualSize": 47632384,
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:78561cef0761903dd2f7d09856150a6d4fb48967a8f113f3e33d79effbf59a07",
                "sha256:c028c01f43bcdf73e1c19b39b44e82c48aed4a0493a1eeb0e965033044d03ffd",
                "sha256:b65aff7ee426a592c62013c7d5a68a6e4eef7cefcfac4c776ab06bcfcd1d51de",
                "sha256:16f2939def5150a32f0f24c9ba38c88051cac30ecdceff241d9335668aecb40c",
                "sha256:9a2d14b22cbe847f6cdfaccefd1cecd725f718eee02e586bfcefb10ff8e4c257",
                "sha256:f3719eb0da5e3c3b53981789684be353a0d79066ea3fdc0c499478f217079331",
                "sha256:2cdd4bacf8275211fb840dece675a378370b1d3bd5f010d2797f338df417eb42",
                "sha256:26d9c958379713439c71d69e079d6d5f4b1c910136cace47f433342efe887ee6"
            ]
        },
        "Metadata": {
            "LastTagTime": "0001-01-01T00:00:00Z"
        }
    }
]

```

[oci-runtime-spec]: https://github.com/opencontainers/runtime-spec
[runc]: https://github.com/opencontainers/runc
