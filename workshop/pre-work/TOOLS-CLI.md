## CLI TOOLS

## Install s2i CLI tool

To install s2i CLI tool,

1. Download tar file.

    ```
	curl -s https://api.github.com/repos/openshift/source-to-image/releases/latest \
	  | grep browser_download_url \
	  | grep linux-amd64 \
	  | cut -d '"' -f 4 \
	  | wget -qi -
    ```

1. Unzip tar file

    ```
	tar xvf source-to-image*.gz
    ```

1. Make s2i CLI accessiblee.

    ```
	sudo mv s2i /usr/local/bin
    ```

1. verify

    ```
	s2i version  
    ```


With that done, you can start the lab.

