CPP=g++ -g 

KERNEL_DIR=../../kernel
LIBPCAP_DIR=../libpcap
INCLUDE=-I$(KERNEL_DIR) -I$(LIBPCAP_DIR) -I../lib `../lib/pfring_config --include`
LIBPFRING_CPP=libpfring_cpp.a
RANLIB=ranlib
OBJ=PFring.o
LIBS=../lib/libpfring.a `../lib/pfring_config --libs` -lpthread

all: $(LIBPFRING_CPP) pf_test

pf_test: pf_test.cpp $(LIBPFRING_CPP)
	$(CPP) $(INCLUDE) $< $(LIBPFRING_CPP) -o $@ $(LIBS) $(LIBPCAP_DIR)/libpcap.a  -lrt

$(LIBPFRING_CPP): $(OBJ)
	@rm -f $@
	ar rc $@ $(OBJ) $(LIBPFRING_CPP)
	$(RANLIB) $@

PFring.o: PFring.cpp PFring.h
	$(CPP) -c $(INCLUDE) $<

clean:
	/bin/rm -f $(TARGET) *.o *~ $(LIBPFRING_CPP) pf_test
