## Functions in Bash Examples
 - Below are some functions written to perform various of tasks:

    ```bash
    ## this function starts apache server and serves a custom page
    serveWebScript(){
        ## pipe heredoc to php script 
        cat << _EOF_ > ~/index.php
        <!DOCTYPE html>
            <html>
            <head>
                <title>PHP Script</title>
                <style>
                h1 {
                    text-align:left;
                }
                </style>
            </head>
            <body>
            <h1>Surname</h1>
                <?php echo '<p>Surname: HAO</p>'; ?>
                <h1>Date Stamp</h1>
                <p>Current date and time in AEST: <?php date_default_timezone_set('Australia/Sydney'); echo date('Y-m-d H:i:s'); ?></p>
                <p>Current date and time in CEST: <?php date_default_timezone_set('Europe/Paris'); echo date('Y-m-d H:i:s'); ?></p>
            </body>
        </html>
        _EOF_
        #placing the file in the directoryroot i.e. /var/www/html/ to set a default page
        mv ~/index.php /var/www/html/
        systemctl restart httpd
        echo "Serving PHP script to Apache server" 
        echo " "
    }

    ## this function creates a swap file with 4GB of space
    addSwapSpace(){
        echo "Adding 4GB of Swap space at /swapfile"
        #mkdir /Swap
        dd if=/dev/zero of=/swapfile bs=200M count=20  
        chmod 600 /swapfile
        mkswap /swapfile
        swapon /swapfile
    }

    ## this function saves function return value to a variable
    testFunctionReturn(){
	local local_fun_return="test value"
	echo $local_fun_return
    }
    

    ##serveWebScript
    ##addSwapSpace
    ##returned_from_func="$(test_function_return)" 
    ```