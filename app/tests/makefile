CC=clang
CFLAGS=-Wall -Wextra -pedantic -O0 -g3 -fsanitize=address
LIBS = -lsqlite3 
NO_DEBUG = -DSUPPRESS_PRINTFS

ALL = main coordinates itinerary struct_mat_adj database_reader create_mat_adj_in_txt borne etape vehicules export simulation

DEPENDENCIES = database_reader.c coordinates.c borne.c etape.c vehicules.c itinerary.c thread.c random_points.c export.c simulation.c
dot=..


tests: $(patsubst %.c,$(dot)/src/%.o,$(DEPENDENCIES)) tests.o $(LIBS)
	$(CC) $(CFLAGS) $(patsubst %.c,$(dot)/src/%.o,$(DEPENDENCIES)) tests.o -o tests $(LIBS)

tests.o : tests.c $(wildcard ../src/*.h)

tests_generation_trajets: $(patsubst %.c,$(dot)/src/%.o,$(DEPENDENCIES)) tests_generation_trajets.o $(LIBS)
	$(CC) $(CFLAGS) $(patsubst %.c,$(dot)/src/%.o,$(DEPENDENCIES)) tests_generation_trajets.o -o tests_generation_trajets $(LIBS)

tests_generation_trajets.o : tests_generation_trajets.c $(wildcard ../src/*.h)

tests_vehicules: $(patsubst %.c,$(dot)/src/%.o,$(DEPENDENCIES)) tests_vehicules.o $(LIBS)
	$(CC) $(CFLAGS) $(patsubst %.c,$(dot)/src/%.o,$(DEPENDENCIES)) tests_vehicules.o -o tests_vehicules $(LIBS)

tests_vehicules.o : tests_generation_trajets.c $(wildcard ../src/*.h)

tests_bornes: $(patsubst %.c,$(dot)/src/%.o,$(DEPENDENCIES)) tests_bornes.o $(LIBS)
	$(CC) $(CFLAGS) $(patsubst %.c,$(dot)/src/%.o,$(DEPENDENCIES)) tests_bornes.o -o tests_bornes $(LIBS)

tests_bornes.o : tests_bornes.c $(wildcard ../src/*.h)


clean : 
	rm -f *.o
	rm -f tests
	rm -f tests_generation_trajets
	rm -f tests_vehicules
	rm -f tests_bornes