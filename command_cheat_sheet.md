# Containerlab/Docker Cheat Sheet

This is a document I use to keep track of all the commands one might need to run (and why). 

### Oops I locked myself out (Arista cEOS)

I sometimes lock myself out of a container. 

`sudo docker exec -it <container name> Cli`

Cli is the shell (think IOS-like) that EOS uses for configuration. You can also specify bash (and then if you want the EOS shell, just type `Cli`). 

