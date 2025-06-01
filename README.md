# Building Miryoku with qmk_userspace

Sofle is of 4x6+5 layout and contains extra keys not used by Miryoku. I want to
keep the Miryoku keys and customise other keys.

In the pre-userspace qmk_firmware directory structure, the Miryoku impl is
mostly in the `users/manna-harbour_miryoku` directory as global setups, and
keyboard specific setup are under `keyboards/[keyboard]/keymaps/manna-harbour_miryoku`.

If you want to build Miryoku layout with customisations, you will need to copy
both these directories and update the keymaps in `keyboards` directory. You can
use `chadluo_miryoku` settings in this repo as a reference.

1. fork and clone [`qmk/qmk_userspace`](https://github.com/qmk/qmk_userspace) repo
1. install Docker Desktop or OrbStack for devcontainer
1. open the repo with vscode, and open in devcontainer when prompted
    - this will automatically install `qmk` in devcontainers, so no need to setup on host
1. in devcontainer terminal, run `qmk setup`
    - it will clone `qmk/qmk_firmware` if not yet
    - at the end you should have two directories:
        - `/workspaces/qmk_userspace` the working directory
        - `/workspaces/qmk_firmware` the firmware clone
1. copy miryoku_qmk user code from [miryoku_qmk/users/manna-harbour_miryoku](https://github.com/manna-harbour/miryoku_qmk/tree/miryoku/users/manna-harbour_miryoku) to `users` directory
1. update `key_overrides` declaration according to [#361](https://github.com/manna-harbour/miryoku/discussions/361)
1. copy miryoku_qmk keyboard code from [miryoku_qmk/keyboards/sofle/keymaps/manna-harbour_miryoku](https://github.com/manna-harbour/miryoku_qmk/tree/miryoku/keyboards/sofle/keymaps/manna-harbour_miryoku) to `keyboards` directory, assuming sofle
1. in devcontainer terminal, run `make sofle:manna-harbour_miryoku`
