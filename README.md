# fsystem
# подготовка и код
Создаем и открываем файл load.S командой:

    nano load.S

код на ассемблере:

    .code16
    .text
         .globl _start;
    _start:
        
        . = _start + 510
        .byte 0x55
        .byte 0xaa
        

Нажимаем contrl + o чтобы сохранить, contrl + x чтобы выйти
Чтобы скомпилировать этот код вводим 

    as load.S -o load.o
    ld -o load load.o
    

    
# отсылка

1 часть урока - https://github.com/aaddvv/gid
    
