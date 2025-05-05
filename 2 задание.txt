field = [['-' for _ in range(3)] for _ in range(3)]
def print_field():
    print("  0 1 2")
    for i, stroka in enumerate(field):
        print(f"{i} {' '.join(stroka)}")
def make_move(stroka, stolb, player):
    if field[stroka][stolb] == '-':
        field[stroka][stolb] = player
    else:
        print("Ячейка занята!")
def play_game():
    current_player = 'x'
    for _ in range(9):
        print_field()
        try:
            stroka = int(input(f"Игрок {current_player}, введите номер строки (0-2): "))
            stolb = int(input(f"Игрок {current_player}, введите номер столбца (0-2): "))
        except ValueError:
            print("Введите числовые значения.")
            continue
        if 0 <= stroka <= 2 and 0 <= stolb <= 2:
            if make_move(stroka, stolb, current_player):
                current_player = 'o' if current_player == 'x' else 'x'
        else:
            print("Некорректный ввод. Диапазон: 0-2")
    print_field()
    print("Игра завершена!")
play_game()
