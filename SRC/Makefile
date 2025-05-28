# -*- tab-width:4 -*-

ASM		= uasm257_x64/uasm64 -q
LINK	= open-watcom-2_0-c-win-x64/binnt64/wlink
PARA	= -j 16

vzibmj:
	$(MAKE) $(PARA) ASM_OPT="-DIBMJ" vz.com

vzibm:
	$(MAKE) $(PARA) ASM_OPT="-DIBMV" vz.com

vz.com: main.obj alias.obj char.obj core.obj disp.obj dos.obj expr.obj \
	filer.obj gets.obj harderr.obj inst.obj key.obj ledit.obj macro.obj \
	memo.obj menu.obj misc.obj open.obj printf.obj scrn.obj smooth.obj \
	string.obj text.obj view.obj wind.obj swap.obj ems.obj xscr.obj msg.obj
	$(LINK) format dos com option quiet,map=mapfile.txt debug dwarf lines name $@ file { $^ }

%.obj: %.asm vz.inc
	$(ASM) -Zm -Zd -nomlib -Zne -fpc $(ASM_OPT) -Fl=$*.lst $<

key.obj: key98.asm keyibm.asm vz.inc

printf.obj: sprintf.inc

scrn.obj: scrn98.asm scrnibm.asm vz.inc

clean:
	rm -rf *.obj *.err *.lst mapfile.txt
