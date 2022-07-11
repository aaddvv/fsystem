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
    
создаем папку для образа диска:

    mkdir disk
    
перемещаем файл системы из прошлого урока в папку

    mv kernel-2 disk
    
создаем образ диска размером 1,4 мб

    dd if=disk of=disk.img bs=512 count=2880
    
копируем загрузочный файл в диск

    dd if=load of=disk.img
    
# доведение компиляции до автоматизма

код:

    nasm -f elf32 kernel.asm -o kasm.o
    gcc -m32 -c kernel.c -o kc.o
    ld -m elf_i386 -T link.ld -o kernel-2 kasm.o kc.o
    as load.S -o load.o
    ld -o load load.o
    mkdir disk
    mv kernel-2 disk
    dd if=disk of=disk.img bs=512 count=2880
    dd if=load of=disk.img

# отсылка

1 часть урока - https://github.com/aaddvv/gid
    
