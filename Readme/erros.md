# Erros

---

# Flex layout
Por algum motivo o angular quebra com o uso do flex layout 
  @angular/flex-layout": "^10.0.0-beta.32"f

# para resolver basta fazer downgrade 

  
    npm i @angular/flex-layout@9.0.0-beta.31

---



#Existem uma erros para o linux que emite varios errors no hot reload 

  >Resolvido  seguindo os comentários  a baixo

 
    ou can fix it, that increasing the amount of inotify watchers.

    If you are not interested in the technical details and only want to get Listen to work:

    If you are running Debian, RedHat, or another similar Linux distribution, run the following in a terminal:

    $ echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p

    If you are running ArchLinux, run the following command instead

    $ echo fs.inotify.max_user_watches=524288 | sudo tee /etc/sysctl.d/40-max-user-watches.conf && sudo sysctl --system

    Then paste it in your terminal and press on enter to run it.

    The Technical Details

    Listen uses inotify by default on Linux to monitor directories for changes. It's not uncommon to encounter a system limit on the number of files you can monitor. For example, Ubuntu Lucid's (64bit) inotify limit is set to 8192.

    You can get your current inotify file watch limit by executing:

    $ cat /proc/sys/fs/inotify/max_user_watches
    When this limit is not enough to monitor all files inside a directory, the limit must be increased for Listen to work properly.

    You can set a new limit temporary with:

    $ sudo sysctl fs.inotify.max_user_watches=524288
    $ sudo sysctl -p
    If you like to make your limit permanent, use:

    $ echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf
    $ sudo sysctl -p
    You may also need to pay attention to the values of max_queued_events and max_user_instances if listen keeps on complaining.


    outra sugestão foi 
      rm -r node_modules
      npm install 


    e tambem 
    echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf 

