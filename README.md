#for maji majo Iris LCD

�}�W�}�W���A�C���X�p��mod �ł��B

�i���C�Z���X�֌W�܂��`�F�b�N���ĂȂ��ł��E�E�E�j


#HOWTO
```
sudo apt-get install bc bison flex libssl-dev libncurses5-dev
sudo wget https://raw.githubusercontent.com/notro/rpi-source/master/rpi-source -O /usr/bin/rpi-source
sudo chmod +x /usr/bin/rpi-source
sudo /usr/bin/rpi-source -q --tag-update
sudo rpi-source
```

/root/����Linux �J�[�l���\�[�X�ꎮ����������܂��B

�܂��A/lib/modules/x.x.x.../build �ɃV���{���b�N�����N���쐬����܂��B

�ȏ�ŁA�J�[�l�����W���[�����r���h�������1�N���b�N�ō��ꂽ���ƂɂȂ�܂��B


�Q�l
https://qiita.com/RCA3610/items/02d8274d78ee8c26e8c9


#�}�W���J�A�C���XLCD�ڑ�


#�h���C�o���r���h

����Afb_s6d1121.c�@�Ƃ����t�@�C�����}�W���J�A�C���X�t���p�ɉ��������Ă��炢�܂����B�i�p�����[�^�x�^���������āE�E�E�j


```
sudo make -j4
```


```
#�h���C�o�����[�h

./majiinsmod.sh

#gpio�̐ڑ�����������΁A�t�����Ó]���܂��B

#�h���C�o���A�����[�h

./majirmmod.sh
```

#�t���[���o�b�t�@�g����

https://github.com/notro/fbtft/wiki/Framebuffer-use

fbcp�Ńf�X�N�g�b�v�ʂ��̂��ʔ����ł��ˁB�@���Ƃ� fbi ��

�icon2fbmap ��sudo raspi-config �̃u�[�g�̂Ƃ�����R���\�[���u�[�g�ɂ��Ȃ��ƁAGUI�u�[�g���Ƃł��Ȃ����H�Ƃ������ł��Ȃ������j

https://qiita.com/kitazaki/items/9f6119d7dc21cd29268e

fbtest�@�i�`��e�X�g�j

���̂�����̃y�[�W���Q�l�ɂȂ�܂��B


```
git clone https://git.kernel.org/pub/scm/linux/kernel/git/geert/fbtest.git
cd fbtest
make
./fbtest --fbdev /dev/fb1
```


#�⑫

```
#fbtft�֘A�̃h���C�o�̓ǂݍ��ݏ󋵊m�F
lsmod | grep fb

#�h���C�o�P�����[�h
sudo insmod xxx
#�h���C�o�P���A�����[�h
sudo rmmod xxx

```



�ȉ��Aoriginal README

  FBTFT
=========

2015-01-19
The FBTFT drivers are now in the Linux kernel staging tree: https://git.kernel.org/cgit/linux/kernel/git/gregkh/staging.git/tree/drivers/staging/fbtft?h=staging-testing
Development in this github repo has ceased.


Linux Framebuffer drivers for small TFT LCD display modules.
The module 'fbtft' makes writing drivers for some of these displays very easy.

Development is done on a Raspberry Pi running the Raspbian "wheezy" distribution.

INSTALLATION
  Download kernel sources

  From Linux 3.15  
    cd drivers/video/fbdev
    git clone https://github.com/notro/fbtft.git
    
    Add to drivers/video/fbdev/Kconfig:   source "drivers/video/fbdev/fbtft/Kconfig"
    Add to drivers/video/fbdev/Makefile:  obj-y += fbtft/
  
  Before Linux 3.15  
    cd drivers/video
    git clone https://github.com/notro/fbtft.git
    
    Add to drivers/video/Kconfig:   source "drivers/video/fbtft/Kconfig"
    Add to drivers/video/Makefile:  obj-y += fbtft/
  
  Enable driver(s) in menuconfig and build the kernel


See wiki for more information: https://github.com/notro/fbtft/wiki


Source: https://github.com/notro/fbtft/
