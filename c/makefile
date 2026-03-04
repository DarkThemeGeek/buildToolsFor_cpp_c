CC = gcc
CFLAGS = -Wall -Wextra -std=c17 -g -MMD -MP

SRC_DIR = src
BUILD_DIR = build
TARGET = app

# Check if include/ exists, otherwise use src/
ifeq ($(wildcard include),include)
    INC_DIR = include
else
    INC_DIR = $(SRC_DIR)
endif

# Check if lib/ exists
ifeq ($(wildcard lib),lib)
    LIB_DIR = lib
    LDFLAGS += -L$(LIB_DIR)
endif

CFLAGS += -I$(INC_DIR)

SRCS = $(wildcard $(SRC_DIR)/*.c)
OBJS = $(SRCS:$(SRC_DIR)/%.c=$(BUILD_DIR)/%.o)

all: $(TARGET)

# Link
$(TARGET): $(OBJS)
	$(CC) $(CFLAGS) -o $@ $(OBJS) $(LDFLAGS)

# Compile into build folder
$(BUILD_DIR)/%.o: $(SRC_DIR)/%.c | $(BUILD_DIR)
	$(CC) $(CFLAGS) -c $< -o $@

# Create build directory
$(BUILD_DIR):
	mkdir -p $(BUILD_DIR)

clean:
	rm -rf $(BUILD_DIR) $(TARGET)

-include $(OBJS:.o=.d)

.PHONY: all clean