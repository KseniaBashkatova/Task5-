# Практическая работа №5: Одномерные массивы в C#, класс System.Array и модульная консольная RPG


### Вариант 9. Тактический спецназ (Штурмовая операция)

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace TacticalAssault
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.OutputEncoding = System.Text.Encoding.UTF8;
            Console.WriteLine("=== Штурмовая операция: Тактический спецназ ===\n");

            // 1. Создание массива боекомплекта бойца tacticalGear на 5 слотов
            string[] tacticalGear = { "Бронежилет", "Светошумовая граната", "Тактическая аптечка", "Тепловизор", "Штурмовой магазин" };

            // 2. Синхронные массивы для 3 рубежей обороны
            string[] sectors = { "Левый фланг (холл)", "Центральный коридор", "Правый фланг (лестница)" };
            int[] enemyCounts = { 1, 1, 1 }; // Часовой, Стрелок, Командир
            int[] enemyHPs = { 30, 75, 130 };

            // 3. Массив времени реакции на угрозу (в миллисекундах)
            int[] reactionTimes = { 420, 315, 550, 290, 380 };

            // 4. Вывод перечня амуниции через цикл foreach
            Console.WriteLine("Текущий боекомплект бойца:");
            foreach (var item in tacticalGear)
            {
                Console.WriteLine($"- {item}");
            }
            Console.WriteLine();

            // 5. Реализация броска "Светошумовая граната"
            Console.WriteLine("Боец выдергивает чеку и бросает светошумовую гранату...");
            int grenadeIndex = Array.IndexOf(tacticalGear, "Светошумовая граната");
            if (grenadeIndex != -1)
            {
                tacticalGear[grenadeIndex] = "Пусто";
                Console.WriteLine("Взрыв! Противники дезориентированы. Слот гранаты очищен.\n");
            }
            else
            {
                Console.WriteLine("Граната не обнаружена в снаряжении.\n");
            }

            // 6. Запись числа попаданий по секторам в массив hitsLog
            // Симуляция штурма: сектор 0 - 12 попаданий, сектор 1 - 25, сектор 2 - 18
            int[] hitsLog = { 12, 25, 18 };
            Console.WriteLine("Результаты штурма по секторам:");
            for (int i = 0; i < sectors.Length; i++)
            {
                Console.WriteLine($"Сектор: {sectors[i]} | Уничтожено целей: {enemyCounts[i]} | Попадания: {hitsLog[i]}");
            }
            Console.WriteLine();

            // 7. Поиск минимального времени реакции (лучший показатель)
            int minReaction = reactionTimes.Min(); // Используем LINQ для краткости (эквивалентно ручному поиску минимума)
            Console.WriteLine($"Лучшее время реакции бойца: {minReaction} мс.\n");

            // 8. Вычисление общего числа попаданий штурмовика
            int totalHits = hitsLog.Sum(); // Используем LINQ (эквивалентно циклу с накоплением)
            Console.WriteLine($"Общее число попаданий штурмовика за операцию: {totalHits}\n");

            // 9. Сортировка массива времени реакции
            Array.Sort(reactionTimes);
            Console.WriteLine("Отсортированные показатели времени реакции (от лучшего к худшему):");
            foreach (var time in reactionTimes)
            {
                Console.WriteLine($"{time} мс");
            }
            Console.WriteLine();

            // 10. Очистка последних 2 слотов снаряжения после форсирования дымовой завесы
            Console.WriteLine("Боец форсирует дымовую завесу. Утрата части снаряжения...");
            // Array.Clear очищает диапазон, начиная с индекса. Длина массива 5, последние два индекса: 3 и 4.
            Array.Clear(tacticalGear, 3, 2);

            Console.WriteLine("\nИтоговое состояние боекомплекта после зачистки:");
            for (int i = 0; i < tacticalGear.Length; i++)
            {
                // Чтобы вывод был наглядным, покажем индексы слотов
                Console.WriteLine($"Слот {i + 1}: {tacticalGear[i]}");
            }

            Console.WriteLine("\n=== Операция завершена. Здание зачищено ===");
            Console.WriteLine("Нажмите любую клавишу для выхода...");
            Console.ReadKey();
        }
    }
}
```
`Результат выполнения:`
<picture>
  <img src="https://github.com/KseniaBashkatova/Task5-/blob/main/assets/screens/PPPP.png?raw=true">
</picture>
```

