# PM (Protected Mode)

Protected mode example
```armasm
cli                   ; disable interrupts
lgdt [gdt_descriptor] ; load the GDT descriptor
mov eax, cr0
or eax, 0x1           ; set PE (Protection Enable) bit in CR0 (Control Register 0)
mov cr0, eax
jmp CODE_SEG:init_pm  ; far jump into GDT, pointing at a 32-bit PM code segment descriptor

[bits 32]
init_pm:
    mov ax, DATA_SEG
                      ; CS register is filled with proper segment values by jump
    mov ds, ax        ; Data Segment
    mov es, ax
    mov fs, ax
    mov gs, ax
    mov ss, ax        ; Stack Segment
```