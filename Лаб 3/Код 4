% ИНДИВИДУАЛЬНОЕ ЗАДАНИЕ 1 (в списке №1 Институт)
% База данных: Студенты, Курсы и Зачисления (связь Многие-ко-Многим)

:- dynamic student/3.     % студент(ID, Name, Group)
:- dynamic course/2.      % курс(CourseID, Title)
:- dynamic enrollment/2.  % зачисление(StudentID, CourseID)

% Инициализация тестовых данных
init_data :-
    retractall(student(_, _, _)),
    retractall(course(_, _)),
    retractall(enrollment(_, _)),
    assertz(student(1, 'Кузнецова Татьяна', 'ЭВМб-23-1')),
    assertz(student(2, 'Бурмакина Валерия', 'ЭВМб-23-1')),
    assertz(student(3, 'Назаров Кирилл', 'ЭВМб-23-2')),
    assertz(course(101, 'Физкультура')),
    assertz(course(102, 'Базы данных')),
    assertz(enrollment(1, 101)),
    assertz(enrollment(1, 102)),
    assertz(enrollment(2, 102)),
    write('>>> Тестовые данные успешно загружены!'), nl.

% Главное меню программы
main :-
    repeat,
    nl, write('=== БАЗА ДАННЫХ: ИНСТИТУТ ==='), nl,
    write('1. Загрузить тестовые данные'), nl,
    write('2. Показать всех студентов'), nl,
    write('3. Показать курсы конкретного студента (Связь N:M)'), nl,
    write('4. Удалить студента и его курсы (Каскадное удаление)'), nl,
    write('0. Выход'), nl,
    write('Выберите пункт: '),
    read(Choice),
    menu_do(Choice),
    Choice == 0, !.

% Обработка пунктов меню
menu_do(1) :- init_data, !. 

menu_do(2) :-
    write('--- Список студентов ---'), nl,
    student(ID, Name, Group),
    write('ID: '), write(ID), write(' | ФИО: '), write(Name), write(' | Группа: '), write(Group), nl,
    fail.
menu_do(2) :- !.

menu_do(3) :-
    write('Введите ID студента: '), read(SearchID),
    ( student(SearchID, Name, _) ->
        write('Студент: '), write(Name), nl, write('Записан на курсы:'), nl,
        ( enrollment(SearchID, CourseID), course(CourseID, Title),
          write(' - '), write(Title), nl, fail
        ; true )
    ; write('Студент с таким ID не найден!'), nl
    ), !.

menu_do(4) :-
    write('Введите ID студента для удаления: '), read(DelID),
    ( student(DelID, Name, _) ->
        retract(student(DelID, _, _)),         % Удаляем студента
        retractall(enrollment(DelID, _)),      % Удаляем его записи на курсы
        write('>>> Студент "'), write(Name), write('" и все его курсы удалены!'), nl
    ; write('Студент не найден!'), nl
    ), !.

menu_do(0) :- write('До свидания!'), nl, !.
menu_do(_) :- write('Ошибка: Неверный пункт меню!'), nl, !.
