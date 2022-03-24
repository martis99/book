# Disk

Reading from disk
```armasm
mov [BOOT_DISK], dl  ; BIOS stores disk number that program was loaded from to dl

mov ax, 0x0240       ; function (0x02 = read), 65 sectors
mov bx, 0x8000       ; write data to 0x8000
mov cx, 0x0002       ; read from cylinder: 0, sector: 2
mov dl, [BOOT_DISK]  ; read from boot disk
xor dh, dh           ; read from head 0
int 0x13             ; read data
jc Error             ; if read failed jump to Error

Error:
    jmp $            ; loop forever

BOOT_DISK db 0

```