CC_SOURCES:=$(filter-out ce.cc ce_long_error.cc,$(wildcard *.cc))
CC_BINARIES:=$(patsubst %.cc,%,$(CC_SOURCES))
JAVA_SOURCES:=$(filter-out Main.java $(wildcard ce*.java),$(wildcard *.java))
JAVA_CLASSES:=$(patsubst %.java,%.class,$(JAVA_SOURCES))

.PHONY: all clean

all: $(CC_BINARIES) $(JAVA_CLASSES)

clean: 
	rm -f $(CC_BINARIES) $(JAVA_CLASSES) guile_loader

$(CC_BINARIES): % : %.cc
	g++ -o $@ -ansi -fno-asm -O2 -Wall -lm --static -s -DONLINE_JUDGE $^

$(JAVA_CLASSES): %.class : %.java
	cp -f $^ Main.java
	javac Main.java
	rm -f Main.java
	mv Main.class $@

ac_multiple_classes.class: ac_multiple_classes.java
	cp -f ac_multiple_classes.java Main.java
	javac Main.java
	rm -f Main.java
	mv Main.class ac_multiple_classes.class
	mv 'Main$$1.class' 'ac_multiple_classes$$1.class'

tle_multiple_classes_static_initializer.class: tle_multiple_classes_static_initializer.java
	cp -f tle_multiple_classes_static_initializer.java Main.java
	javac Main.java
	rm -f Main.java
	mv Main.class tle_multiple_classes_static_initializer.class
	mv 'T.class' 'tle_multiple_classes_static_initializer_T.class'
