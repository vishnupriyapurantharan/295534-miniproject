PROJ_NAME = binary_calculator

TEST_PROJ_NAME = Test_$(PROJ_NAME)

BUILD_DIR = ./Build

ifdef OS
   RM = del /q
   FixPath = $(subst /,\,$1)
   EXEC = exe
else
   ifeq ($(shell uname), Linux)
      RM = rm -rf
      FixPath = $1
	  EXEC = out
   endif
endif 


SRC =  src/Binary_to_Decimal.c src/Binary_to_Octal.c src/Decimal_to_Binary.c src/Decimal_to_Octal.c src/Octal_to_Binary.c src/Octal_to_Decimal.c

INC = -Iinc\
-Iunity

UNITY = unity/unity.c 

testest_filest = test/test_main.c

pro: main.c $(SRC) 
	gcc main.c $(SRC) -I $(INC) -o pro.exe

run: pro.exe
	./pro.exe

test: $(SRC) test_files/test_main.c  $(UNITY)
	gcc $^ $(INC) -o $(call FixPath,$(BUILD_DIR)/$(TEST_PROJ_NAME).$(EXEC))
	$(call FixPath,$(BUILD_DIR)/$(TEST_PROJ_NAME).$(EXEC))

coverage:${PROJECT_NAME}
	gcc -fprofile-arcs -ftest-coverage main.c $(SRC) $(INC) -o $(call FixPath,$(BUILD_DIR)/$(TEST_PROJ_NAME).$(EXEC))
	$(call FixPath,$(BUILD_DIR)/$(TEST_PROJ_NAME).$(EXEC))
	gcov -a main.c $(SRC) $(call FixPath,$(BUILD_DIR)/$(TEST_PROJ_NAME).$(EXEC))
	$(RM) *.gcno
	$(RM) *.gcov
	$(RM) *.gcda

   
#test1: test_files\test_main.c $(SRC) unity\unity.c 
#	gcc test_files\test_main.c $(SRC) unity\unity.c -I $(INC) -I $(UNITY) -o test.exe

#test_run: test.exe
#	./test.exe

clean:
	$(RM) *.exe
