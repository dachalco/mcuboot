To sign

../../../scripts/imgtool.py sign --key ../../../root-ec-p256.pem --header-size 32 --align 4 --version 1.1 --slot-size 0x64000 --pad-header --pad aws_demos.1.hex signed_aws_demos.1.hex

To flash
    pyocd erase --sector 0x27000-0x8c000 --target nrf52 --verbose    
    pyocd flash -a 0x27020 signed_aws_demos1.hex --target nrf52
    pyocd flash -a 0x4f020 signed_aws_demos2.hex --target nrf52
