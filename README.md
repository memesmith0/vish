#!/bin/sh
#this shell is a shell that perpetually runs vi to open a shell script of your choosing
#as soon as you exit vi that shell script is immediately run and piped into less to view its output
#as soon as that is done you loop back into vi to edit the file again. this cycle continues forever.
#I dont currently have a way to exit
#I think I could some how use eval an an additional loop to create a way to exit and this seems more natural. I dont want to make that right now so for now there is now ay to exit.
#for now vish depends on edtrnlp
edtrnlp(){ while : ; do edtrnlp_file="/dev/shm/edtrnlp_output_$$" && "$1" "$3" && "$2" "$3" > "$edtrnlp_file" && "$1" "$edtrnlp_file" && rm "$edtrnlp_file" ; done ; } &&
vish(){ edtrnlp vi sh "$1" ; } &&
vish ;
