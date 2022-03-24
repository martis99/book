# Print

Printing
```armasm
mov ah, 0x0E  ; set function to display char
mov al, 'H'   ; set char to 'H'
int 0x10      ; display
```