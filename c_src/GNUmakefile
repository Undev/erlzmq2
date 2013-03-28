LINUX=$(shell uname | grep -E "(Linux|NetBSD)" | wc -l | xargs echo)
DEPS=../deps

ifeq ($(LINUX),1)
ZMQ_FLAGS=--with-pic
else
ZMQ_FLAGS=
endif

all: $(DEPS)/zeromq2/src/.libs/libzmq.a

clean:
	if test -e $(DEPS)/zeromq2/Makefile; then \
		cd $(DEPS)/zeromq2; make clean; \
	else \
		true; \
	fi

distclean:
	@rm -rf $(DEPS)

$(DEPS)/zeromq2/src/.libs/libzmq.a:
	@cd $(DEPS)/zeromq2 && ./autogen.sh && ./configure $(ZMQ_FLAGS) && make
