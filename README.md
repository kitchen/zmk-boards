various boards and shields I've played around with

# building

this doesn't have github actions because I'm using this with local build environments.

The way I'm doing it is with a `[docker-compose.yml](https://github.com/zmkfirmware/zmk/pull/879 "PR to ZMK for docker-compose workflow")` file in the root of the zmk repo and using `docker compose run` to execute a shell inside the environment.

From within the zmk repo:

``` sh
docker compose up -d
docker compose run -v ~/Development/zmk-boards/breadkitchen/config:/workspace/config shell bash
```

Then to actually build the board:

``` sh
cd workspace/app
west build -b nice_nano_v2 -- -DSHIELD=breadkitchen -DZMK_CONFIG=/workspace/config
```

This will leave a zmk.uf2 file in the build/zephyr directory.

# breadkitchen

This is a nice!nano powered keyboard-in-a-breadboard experimentation platform thinger.
