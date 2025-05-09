# Модель данных ИС "Делопроизводство"

## ER-диаграмма

### Основные сущности и их связи

1. **Документ**
   - *Связи:*
     - Создается Сотрудником (M:1)
     - Может быть связан с другими Документами (M:M)
     - Может иметь несколько Задач (1:M)
     - Принадлежит к Типу документа (M:1)
     - Может содержаться в нескольких Папках (M:M)

2. **Сотрудник**
   - *Связи:*
     - Относится к Подразделению (M:1)
     - Создает Документы (1:M)
     - Исполняет Задачи (1:M)
     - Имеет Права доступа (1:M)

3. **Подразделение**
   - *Связи:*
     - Включает Сотрудников (1:M)
     - Имеет руководителя (Сотрудник) (1:1)

4. **Задача**
   - *Связи:*
     - Относится к Документу (M:1)
     - Назначается Сотруднику (M:1)

5. **Контрагент**
   - *Связи:*
     - Связан с Документами (1:M)

6. **Папка документов**
   - *Связи:*
     - Может содержать Документы (M:M)
     - Может иметь родительскую Папку (M:1)
     - Имеет владельца (Сотрудник) (M:1)

7. **Шаблон документа**
   - *Связи:*
     - Используется для создания Документов (1:M)
     - Относится к Типу документа (M:1)

8. **Маршрут согласования**
   - *Связи:*
     - Применяется к Документу (M:1)
     - Содержит Этапы согласования (1:M)

9. **Этап согласования**
   - *Связи:*
     - Входит в Маршрут согласования (M:1)
     - Назначается Сотруднику (M:1)

10. **Право доступа**
    - *Связи:*
      - Предоставляется Сотруднику (M:1)
      - Относится к Документу или Папке (M:1)
