# Практическая работа №5: Одномерные массивы в C#, класс System.Array и модульная консольная RPG


### Вариант 9. Тактический спецназ (Штурмовая операция)

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp10
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("=== ТАКТИЧЕСКАЯ ОПЕРАЦИЯ: ШТУРМ ЗДАНИЯ ===\n");

            // ИНЖЕНЕР ИНВЕНТАРЯ (Студент 1)
            // 1. Создать массив боекомплекта бойца tacticalGear на 5 слотов.
            string[] tacticalGear = { "Бронежилет", "Светошумовая граната", "Тактическая аптечка", "Тепловизор", "Штурмовой магазин" };

            // 4. Вывести перечень амуниции через цикл foreach.
            Console.WriteLine("Текущая амуниция бойца:");
            foreach (string item in tacticalGear)
            {
                Console.WriteLine($"- {item}");
            }
            Console.WriteLine();

            // 5. Реализовать бросок "Светошумовая граната": проверка через Array.IndexOf и замена на "Пусто".
            UseItem(tacticalGear, "Светошумовая граната");

            // 10. Очистить последние 2 слота снаряжения через Array.Clear после форсирования дымовой завесы.
            // Очищаем 2 элемента, начиная с индекса 3 (4-й и 5-й слоты).
            Array.Clear(tacticalGear, 3, 2);
            Console.WriteLine("\nПосле форсирования дымовой завесы очищены слоты 4 и 5:");
            foreach (string item in tacticalGear)
            {
                Console.WriteLine($"- {item ?? "Пусто"}");
            }
            Console.WriteLine();

            // ИНЖЕНЕР БОЕВОЙ ЛОГИКИ (Студент 2)
            // 2. Задать синхронные массивы для 3 рубежей обороны: сектор, численность живой силы, секторный урон.
            string[] sectors = { "Главный холл", "Серверная", "Крыша" };
            int[] enemyCounts = { 4, 2, 1 };
            int[] sectorDamage = { 15, 40, 60 }; // Урон, который наносят противники в этих секторах

            // 3. Создать массив времени реакции на угрозу reactionTimes (в миллисекундах) на 5 выходов из-за угла.
            int[] reactionTimes = { 450, 210, 670, 180, 330 };

            // 6. Записать число попаданий по секторам в целочисленный массив hitsLog.
            // Симуляция штурма: сколько точных выстрелов сделал боец в каждом секторе
            int[] hitsLog = { 12, 5, 2 };

            // 7. Найти минимальное время реакции (лучший показатель бойца) в массиве reactionTimes.
            // Ручной поиск минимума (как в теоретической шпаргалке)
            int bestReaction = reactionTimes[0];
            for (int i = 1; i < reactionTimes.Length; i++)
            {
                if (reactionTimes[i] < bestReaction)
                {
                    bestReaction = reactionTimes[i];
                }
            }
            Console.WriteLine($"Лучшее время реакции (минимальное): {bestReaction} мс");

            // 8. Вычислить общее число попаданий штурмовика по всем секторам.
            int totalHits = 0;
            foreach (int hit in hitsLog)
            {
                totalHits += hit;
            }
            Console.WriteLine($"Общее число попаданий по всем секторам: {totalHits}\n");

            // 9. Отсортировать массив времени реакции бойца методом Array.Sort.
            Console.WriteLine("Сортировка времени реакции (от худшего к лучшему):");
            Console.WriteLine("До: " + string.Join(", ", reactionTimes));
            Array.Sort(reactionTimes); // Сортирует по возрастанию
            Console.WriteLine("После Array.Sort: " + string.Join(", ", reactionTimes));

            // Для наглядности развернем массив, чтобы увидеть рейтинг от лучшего к худшему
            Array.Reverse(reactionTimes);
            Console.WriteLine("После Array.Reverse (рейтинг от лучшего к худшему): " + string.Join(", ", reactionTimes));
            Console.WriteLine();

            // Вывод аналитической сводки по рубежам обороны
            Console.WriteLine("=== АНАЛИТИКА РУБЕЖЕЙ ОБОРОНЫ ===");
            for (int i = 0; i < sectors.Length; i++)
            {
                Console.WriteLine($"Сектор: {sectors[i]} | Живая сила: {enemyCounts[i]} | Потенциальный урон: {sectorDamage[i]} | Ваши попадания: {hitsLog[i]}");
            }
        }

        /// <summary>
        /// Пытается найти предмет в экипировке и заменить его на "Пусто".
        /// Демонстрирует работу Array.IndexOf и прямую индексацию.
        /// </summary>
        /// <param name="gear">Массив экипировки.</param>
        /// <param name="itemName">Название искомого предмета.</param>
        static void UseItem(string[] gear, string itemName)
        {
            Console.WriteLine($"\nДействие: Поиск и применение '{itemName}'...");

            // Array.IndexOf возвращает -1, если элемент не найден
            int slotIndex = Array.IndexOf(gear, itemName);

            if (slotIndex != -1)
            {
                Console.WriteLine($"Предмет '{itemName}' найден в слоте {slotIndex + 1}. Применение...");
                // Замена конкретного элемента по индексу
                gear[slotIndex] = "Пусто";
            }
            else
            {
                Console.WriteLine($"Ошибка: '{itemName}' не обнаружена в боекомплекте.");
            }

        }
    }
}

```
