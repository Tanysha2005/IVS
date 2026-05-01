% ИНДИВИДУАЛЬНОЕ ЗАДАНИЕ (в списке №6)

% верисия 1: полный перебор
% любая расстановка ферзей.
solve_naive(Queens) :-
    permutation([1,2,3,4,5,6,7,8], Queens), 
    safe(Queens).                           % бьют ли они друг друга
safe([]).
% проверка, что первый ферзь Q не бьет остальных Qs.
safe([Q|Qs]) :-
    safe(Qs),
    not_attack(Q, Qs, 1).
% если список пуст, ферзь никого не бьет.
not_attack(_,[], _).
% проверка, что ферзи не бьют друг друга по диагонали.
not_attack(X,[Y|Ys], Dist) :-
    abs(X - Y) =\= Dist,      % разница координат не должна быть равна дистанции
    Dist1 is Dist + 1,
    not_attack(X, Ys, Dist1). % проверяем следующих ферзей

% верисия 2: усовершенствованный алгоритм
% добавка ферзей по одному.
solve_optimized(Queens) :-
    place_queens([1,2,3,4,5,6,7,8],[], Queens).
% если не осталось свободных линий, доска заполнена.
place_queens([], Board, Board).
% берем одного ферзя Q, проверяем его, идем дальше.
place_queens(Available, Board, Queens) :-
    select(Q, Available, Rest),   % берем одну цифру из доступных
    not_attack(Q, Board, 1),      % проверка: бьет ли он уже стоящих
    place_queens(Rest, [Q|Board], Queens). % если безопасно, ставим следующего

% вспомогательные предикаты для времени
run_naive(Count) :-
    time(findall(Q, solve_naive(Q), Solutions)),
    length(Solutions, Count).

run_optimized(Count) :-
    time(findall(Q, solve_optimized(Q), Solutions)),
    length(Solutions, Count).
