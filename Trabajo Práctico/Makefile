# Nombre del ejecutable final
TARGET = server

# Directorios
SRC_DIR = src
INCLUDE_DIR = inc
BUILD_DIR = bin

# Archivos fuente y objetos
SRC_FILES = $(wildcard $(SRC_DIR)/*.c)
OBJ_FILES = $(patsubst $(SRC_DIR)/%.c, $(BUILD_DIR)/%.o, $(SRC_FILES))

# Compilador y flags
CC = gcc
CFLAGS = -Wall -std=c99 -pedantic -I$(INCLUDE_DIR)

# Regla para compilar el ejecutable final
$(BUILD_DIR)/$(TARGET): $(OBJ_FILES)
	@mkdir -p $(BUILD_DIR)
	$(CC) -o $@ $^
	@echo "Executable $@ created."

# Regla para compilar cada archivo .c a .o
$(BUILD_DIR)/%.o: $(SRC_DIR)/%.c | $(BUILD_DIR)
	$(CC) $(CFLAGS) -c $< -o $@
	@echo "Compiled $< to $@"

# Crear el directorio de build si no existe
$(BUILD_DIR):
	@mkdir -p $(BUILD_DIR)

# Limpieza de archivos compilados
clean:
	rm -rf $(BUILD_DIR)/*
	@echo "Archives in $(BUILD_DIR) deleted."

# Ejecución del programa
run: $(BUILD_DIR)/$(TARGET)
	@echo "Executing $<..."
	@./$(BUILD_DIR)/$(TARGET)

# PHONY para evitar conflictos con archivos llamados igual
.PHONY: clean run
