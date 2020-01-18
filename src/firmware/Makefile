fw =  qed_init_values_zipped-8.7.3.0.bin

firmware: $(fw)

install: $(fw)
	for f in $+; do \
		install -m 644 -D $$f $(INSTALL_PATH)/lib/firmware/$$f; \
	done

%:: %.ihex
	objcopy -Iihex -Obinary $< $@

%.fw: %.HEX ihex2fw
	./ihex2fw $< $@

%.fw: %.H16 ihex2fw
	./ihex2fw -w $< $@

ihex2fw: ihex2fw.c
	gcc -o $@ $<
