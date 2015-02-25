# Copyright 2014 Matt T. Proud (matt.proud@gmail.com)
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

include ../Makefile.INCLUDE

all: entrypoint.c.disassembled entrypoint.c.elfheader entrypoint.disassembled entrypoint.elfheader

entrypoint: entrypoint.go
	$(GO_BUILD) $<

entrypoint.c.bin: entrypoint.c
	$(CC) $< -static -o $@

entrypoint.c.elfheader: entrypoint.c.bin
	$(READELF) -h $< > $@

entrypoint.c.disassembled: entrypoint.c.bin
	$(OBJDUMP) -M reg-names-raw -d -f $< > $@

entrypoint.elfheader: entrypoint
	$(READELF) -h $< > $@

entrypoint.disassembled: entrypoint
	$(OBJDUMP) -M reg-names-raw -d -f $< > $@

clean:
	rm -f entrypoint.c.bin entrypoint.c.disassembled entrypoint.c.elfheader entrypoint.disassembled entrypoint.elfheader

.PHONY: clean
