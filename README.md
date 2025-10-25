## Telegram Web K
基于 Webogram，经过修补和改进。在这里为所有人提供：https://web.telegram.org/k/


### 开发
安装依赖：
```lang=bash
pnpm install
```
这将安装所有必需的依赖项。


#### 运行 Web 服务器
只需运行 `pnpm start` 来启动 Web 服务器和热重载任务。
在浏览器中打开 http://localhost:8080/。


#### 生产环境运行

运行 `node build` 来构建应用的最小化生产版本。将 `public` 文件夹内容复制到您的 Web 服务器。

### 在 Docker 中运行

#### 开发环境：
* 安装依赖 `docker-compose up tweb.dependencies`。
* 运行开发容器 `docker-compose up tweb.develop`。
* 在浏览器中打开 http://localhost:8080/。

#### 生产环境：
* 运行 `docker-compose up tweb.production -d` nginx 镜像和容器来提供构建服务
* 在浏览器中打开 http://localhost:80/。


我还创建了一个基于 Nginx 的镜像 https://hub.docker.com/r/elgammalx/tweb/tags，可以直接部署。

您可以使用 `docker build -f ./.docker/Dockerfile_production -t {dockerhub-username}/{imageName}:{latest} .` 来构建您的生产就绪镜像。

# 使用

```yaml
services:
  tweb.production:
    image: ghcr.io/scys/tweb:latest
    ports:
      - 8080:80
```

### 依赖项
* [BigInteger.js](https://github.com/peterolson/BigInteger.js) ([Unlicense](https://github.com/peterolson/BigInteger.js/blob/master/LICENSE))
* [pako](https://github.com/nodeca/pako) ([MIT License](https://github.com/nodeca/pako/blob/master/LICENSE))
* [cryptography](https://github.com/spalt08/cryptography) ([Apache License 2.0](https://github.com/spalt08/cryptography/blob/master/LICENSE))
* [emoji-data](https://github.com/iamcal/emoji-data) ([MIT License](https://github.com/iamcal/emoji-data/blob/master/LICENSE))
* [twemoji-parser](https://github.com/twitter/twemoji-parser) ([MIT License](https://github.com/twitter/twemoji-parser/blob/master/LICENSE.md))
* [rlottie](https://github.com/rlottie/rlottie.github.io) ([MIT License](https://github.com/Samsung/rlottie/blob/master/licenses/COPYING.MIT))
* [fast-png](https://github.com/image-js/fast-png) ([MIT License](https://github.com/image-js/fast-png/blob/master/LICENSE))
* [opus-recorder](https://github.com/chris-rudmin/opus-recorder) ([BSD License](https://github.com/chris-rudmin/opus-recorder/blob/master/LICENSE.md))
* [Prism](https://github.com/PrismJS/prism) ([MIT License](https://github.com/PrismJS/prism/blob/master/LICENSE))
* [Solid](https://github.com/solidjs/solid) ([MIT License](https://github.com/solidjs/solid/blob/main/LICENSE))
* [TinyLD](https://github.com/komodojp/tinyld) ([MIT License](https://github.com/komodojp/tinyld/blob/develop/license))
* [libwebp.js](https://libwebpjs.appspot.com/)
* fastBlur
* [mp4-muxer](https://github.com/Vanilagy/mp4-muxer) ([MIT License](https://github.com/Vanilagy/mp4-muxer/blob/main/LICENSE))

### Debugging
You are welcome in helping to minimize the impact of bugs. There are classes, binded to global context. Look through the code for certain one and just get it by its name in developer tools.
Source maps are included in production build for your convenience.

#### Additional query parameters
* **test=1**: to use test DCs
* **debug=1**: to enable additional logging
* **noSharedWorker=1**: to disable Shared Worker, can be useful for debugging
* **http=1**: to force the use of HTTPS transport when connecting to Telegram servers

Should be applied like that: http://localhost:8080/?test=1

#### Taking local storage snapshots
You can also take and load snapshots of the local storage and indexed DB using the `./snapshot-server` [mini-app](/snapshot-server/README.md). Check the `README.md` under this folder for more details.

#### Preview all icons
You can see all the available svg icons by calling the `showIconLibrary()` global function in the browser's console.

### Troubleshooting & Suggesting

If you find an issue with this app or wish something to be added, let Telegram know using the [Suggestions Platform](https://bugs.telegram.org/c/4002).

### Licensing

The source code is licensed under GPL v3. License is available [here](/LICENSE).
