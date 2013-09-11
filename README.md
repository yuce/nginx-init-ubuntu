# nginx-init-ubuntu #

Tried and true Nginx init script.

Adapted from [Jason Giedymin](http://jasongiedymin.com) <jasong -_at_- apache -=dot=- org>


## Last tested with:

1. Ubuntu 12.10
2. [nginx-1.5.4](http://nginx.org/download/nginx-1.5.4.tar.gz)


## Basic Install ##
Basic install instructions, use sudo when necessary. Installs to `/srv`.

    useradd nginx
    sudo apt-get install build-essential libpcre3-dev libssl-dev libgeoip-dev
    cd ~
    curl -O http://nginx.org/download/nginx-1.5.4.tar.gz
    tar xzvf nginx-1.5.4.tar.gz
    cd nginx-1.5.4/
    ./configure --prefix=/srv --user=nginx --group=nginx --with-http_ssl_module --with-http_geoip_module
    make
    sudo make install

    curl -O 'https://raw.github.com/yuce/nginx-init-ubuntu/master/nginx'
    sudo mv nginx /etc/init.d
    sudo chmod +x /etc/init.d/nginx

    service nginx status  # to poll for current status
    service nginx stop    # to stop any servers if any
    service nginx start   # to start the server
    
    #[optional] 
    sudo update-rc.d -f nginx defaults

    #[optional remove the upstart script]
    sudo update-rc.d -f nginx remove

