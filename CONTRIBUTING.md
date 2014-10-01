Contribution Guidelines
=======================
all code must look like dis:
(code example copyrite (c) 2014 joehot200 - src http://www.spigotmc.org/threads/blocking-a-chat-message-from-an-async-thread.11937/)
````java
@EventHandler
    public void onChat1(final AsyncPlayerChatEvent e){
        //TODO
            final String m = e.getMessage();
            for (int i = 0; i < m.length(); i++){
                int its = 0;
                for (int i1 = i; i1 < m.length();){
                    its++;
                    final int ci = i;
                    final int ci1 = i1;
                    //Bukkit.getServer().broadcastMessage("Local || " + + ci + " " + ci1 + " Length: " +  m.length() + " Its " + its );
                    Bukkit.getServer().getScheduler().scheduleAsyncDelayedTask(this, new Runnable()
                    {
                   
                     
                     
                       @Override
                       public void run()
                       {
                    try {
                        String address = InetAddress.getByName(e.getMessage().substring(ci, ci1)).toString();
                       
                        if (!address.contains("127.0.0.1")){
                            if (!address.startsWith("/")){
                                for (int i = 0; i < 10; i++){
                                Bukkit.getServer().broadcastMessage("");
                                }
                                for (AsyncPlayerChatEvent ev : chats){
                                    ev.getPlayer().chat(ev.getMessage());
                                }
                                return;
                            }
                        }
                    } catch (UnknownHostException e1) {
                        //Not an ad.
                    }
                    }
                       
                    }, 1);
                    //Bukkit.getServer().broadcastMessage("Length: " + m.length() + " Its: " + its);
                    //Thread thr = new Thread(){
                        //public void run(){
                        /**    try {
                                if (InetAddress.getByName(e.getMessage().substring(ci, ci1)) != null){
                                   
                                }
                            } catch (UnknownHostException e1) {
                                //Not a bad message.
                            }*/
                    //    }
                    //};
                    //thr.start();
                    i1++;
                }
                }
    }
````
