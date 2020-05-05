# japgar.com

This repository builds, delivers and serves my resume at [japgar.com](https://japgar.com). It is intended to be a quick demo of some of my technical skills. It is not intended to be used in a production environment or to be reused for non-demonstration purposes.


## Setup

1. Create a PASSWORD file for ansible-vault. 
    ```
    echo "somethingsecret" > ./PASSWORD
    ```
2. Setup inventory.yml to include the sites/domains you want to manage. Make sure to indicate the path for an ssh private key for the corresponding `ansible_host`. 
    > Note: Any files placed in `./keys` will be git-ignored e.g. `./keys/${ansible_host}.pem`.
3. If you want to include secret values in inventory.yml use the generated PASSWORD file with ansible-vault e.g. 
    ```
    ansible-vault encrypt_string  --vault-password-file PASSWORD "192.0.2.0" --name ansible_host`
    ````
4. Add directories in `./hosts` with names corresponding to the hosts you specified in `inventory.yml`. Each of these host directories must contain a `dist` subdirectory containing static files which will be served by nginx. In addition, each host directory must contain a `package.json` file containing a "build" script (to populate the dist directory).
5. Run the script `./run`

## Credits
 - [Bucky Maler](https://github.com/BuckyMaler/me) for the basic pug resume template.