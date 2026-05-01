; Экспертная система: Выбор языка программирования
; старт
(defrule start
  =>
  (printout t "Хотите разрабатывать веб-сайты? (yes/no): ")
  (assert (web (read))))
  
; правила ветвления 
(defrule web-yes
  (web yes)
  =>
  (printout t "Вам нравится визуальный дизайн и интерфейсы? (yes/no): ")
  (assert (design (read))))

(defrule web-no
  (web no)
  =>
  (printout t "Хотите создавать видеоигры? (yes/no): ")
  (assert (games (read))))

; выводы советов 
(defrule frontend
  (design yes)
  =>
  (printout t "экспертный совет:" crlf)
  (printout t "Вам стоит изучить JavaScript" crlf))

(defrule backend
  (design no)
  =>
  (printout t "экспертный совет:" crlf)
  (printout t "Вам стоит изучить Python или PHP" crlf))

(defrule games-yes
  (games yes)
  =>
  (printout t "экспертный совет:" crlf)
  (printout t "Вам стоит изучить C# или C++" crlf))

(defrule games-no
  (games no)
  =>
  (printout t "экспертный совет:" crlf)
  (printout t "Вам стоит изучить Python для ИИ или Prolog для сложных логических задач" crlf))
