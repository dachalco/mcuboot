Images
    aws_demo.1.bin - Prints "Hello world 1"
    aws_demo.2.bin - Prints "Hello world 2"
    aws_demo.3.bin - Prints "Hello world 3" and confirms itself with boot_set_confirmed    

To sign
    ../../../scripts/imgtool.py sign --key ../../../root-ec-p256.pem --header-size 32 --align 4 --version 1.1 --slot-size 0x24000 --pad-header --pad aws_demos.1.bin signed_aws_demos.1.bin

To flash
    pyocd erase --sector 0x27000-0x8c000 --target nrf52 --verbose    
    pyocd flash -a 0x27000 signed_aws_demos.1.bin --target nrf52
    pyocd flash -a 0x50000 signed_aws_demos.2.bin --target nrf52
