# Рабочий лист

## Установить видимость столбца {#SetColVisible}

```go
func (f *File) SetColVisible(sheet, col string, visible bool) error
```

SetColVisible предоставляет функцию для установки видимости одного столбца с помощью имени рабочего листа и имени столбца. Например, скройте столбец `D` в `Sheet1`:

```go
err := f.SetColVisible("Sheet1", "D", false)
```

Скрыть столбцы от `D` до `F` (включить):

```go
err := f.SetColVisible("Sheet1", "D:F", false)
```

## Установить ширину столбца {#SetColWidth}

```go
func (f *File) SetColWidth(sheet, startcol, endcol string, width float64) error
```

SetColWidth предоставляет функцию для установки ширины одного столбца или нескольких столбцов. Например:

```go
f := excelize.NewFile()
err := f.SetColWidth("Sheet1", "A", "H", 20)
```

## Установить высоту строки {#SetRowHeight}

```go
func (f *File) SetRowHeight(sheet string, row int, height float64) error
```

SetRowHeight предоставляет функцию для установки высоты одной строки. Например, установите высоту первой строки в `Sheet1`:

```go
err := f.SetRowHeight("Sheet1", 1, 50)
```

## Установить видимость линии {#SetRowVisible}

```go
func (f *File) SetRowVisible(sheet string, row int, visible bool) error
```

SetRowVisible предоставляет функцию для отображения видимости одной строки с помощью заданного имени листа и индекса строки. Например, скройте строку `2` в `Sheet1`:

```go
err := f.SetRowVisible("Sheet1", 2, false)
```

## Получить имя листа {#GetSheetName}

```go
func (f *File) GetSheetName(index int) string
```

GetSheetName предоставляет функцию для получения имени рабочего листа XLSX с помощью указанного индекса рабочего листа. Если заданный индекс листа недействителен, он вернет пустую строку.

## Получить видимость столбца {#GetColVisible}

```go
func (f *File) GetColVisible(sheet, column string) (bool, error)
```

GetColVisible предоставляет функцию, чтобы получить видимость одного столбца с помощью имени рабочего листа и имени столбца. Например, получите видимое состояние столбца `D` в `Sheet1`:

```go
visible, err := f.GetColVisible("Sheet1", "D")
```

## Получить ширину столбц {#GetColWidth}

```go
func (f *File) GetColWidth(sheet, col string) (float64, error)
```

GetColWidth предоставляет функцию для получения ширины столбца с помощью имени рабочего листа и индекса столбца.

## Получить высоту строки {#GetRowHeight}

```go
func (f *File) GetRowHeight(sheet string, row int) (float64, error)
```

GetRowHeight предоставляет функцию для получения высоты строки с помощью заданного имени листа и индекса строки. Например, получить высоту первой строки в `Sheet1`:

```go
height, err := f.GetRowHeight("Sheet1", 1)
```

## Получить видимость строки {#GetRowVisible}

```go
func (f *File) GetRowVisible(sheet string, row int) (bool, error)
```

GetRowVisible предоставляет функцию, чтобы получить видимость одной строки, указав имя листа и индекс строки. Например, получить видимое состояние строки `2` в `Sheet1`:

```go
err := f.GetRowVisible("Sheet1", 2)
```

## Получить индекс рабочего листа {#GetSheetIndex}

```go
func (f *File) GetSheetIndex(name string) int
```

GetSheetIndex предоставляет функцию для получения индекса рабочего листа XLSX с помощью имени листа. Если заданное имя листа недопустимо, возвращается целочисленное значение типа `0`.

Полученный индекс может использоваться как параметр для вызова функции [`SetActiveSheet()`](workbook.md#SetActiveSheet) при настройке рабочего листа по умолчанию для рабочей книги.

## Получить список рабочих листов {#GetSheetMap}

```go
func (f *File) GetSheetMap() map[int]string
```

GetSheetMap предоставляет функцию для получения имен листов и диаграмм и карты индекса XLSX. Например:

```go
f, err := excelize.OpenFile("./Book1.xlsx")
if err != nil {
    return
}
for index, name := range f.GetSheetMap() {
    fmt.Println(index, name)
}
```

## Задать имя листа {#SetSheetName}

```go
func (f *File) SetSheetName(oldName, newName string)
```

SetSheetName предоставляет функцию для установки имени листа по заданным именам старого и нового листа. В заголовке листа допускается не более 31 символа, и эта функция изменяет только имя листа и не обновляет имя листа в формуле или ссылке, связанной с ячейкой. Таким образом, может быть ошибка формулы проблемы или отсутствует ссылка.

## Установить свойства листа {#SetSheetPrOptions}

```go
func (f *File) SetSheetPrOptions(name string, opts ...SheetPrOption) error
```

SetSheetPrOptions предоставляет функцию для установки свойств листа.

Доступные Варианты:

|Необязательный атрибут|Тип|
|---|---|
|CodeName|string|
|EnableFormatConditionsCalculation|bool|
|Published|bool|
|FitToPage|bool|
|AutoPageBreaks|bool|
|OutlineSummaryBelow|bool|

Например:

```go
f := excelize.NewFile()
const sheet = "Sheet1"

if err := f.SetSheetPrOptions(sheet,
    excelize.CodeName("code"),
    excelize.EnableFormatConditionsCalculation(false),
    excelize.Published(false),
    excelize.FitToPage(true),
    excelize.AutoPageBreaks(true),
    excelize.OutlineSummaryBelow(false),
); err != nil {
    panic(err)
}
```

## Получить свойства листа {#GetSheetPrOptions}

```go
func (f *File) GetSheetPrOptions(name string, opts ...SheetPrOptionPtr) error
```

GetSheetPrOptions обеспечивает функцию для получения свойств листа.

|Необязательный атрибут|Тип|
|---|---|
|CodeName|string|
|EnableFormatConditionsCalculation|bool|
|Published|bool|
|FitToPage|bool|
|AutoPageBreaks|bool|
|OutlineSummaryBelow|bool|

Например:

```go
f := excelize.NewFile()
const sheet = "Sheet1"

var (
    codeName                          excelize.CodeName
    enableFormatConditionsCalculation excelize.EnableFormatConditionsCalculation
    published                         excelize.Published
    fitToPage                         excelize.FitToPage
    autoPageBreaks                    excelize.AutoPageBreaks
    outlineSummaryBelow               excelize.OutlineSummaryBelow
)

if err := f.GetSheetPrOptions(sheet,
    &codeName,
    &enableFormatConditionsCalculation,
    &published,
    &fitToPage,
    &autoPageBreaks,
    &outlineSummaryBelow,
); err != nil {
    panic(err)
}
fmt.Println("Defaults:")
fmt.Printf("- codeName: %q\n", codeName)
fmt.Println("- enableFormatConditionsCalculation:", enableFormatConditionsCalculation)
fmt.Println("- published:", published)
fmt.Println("- fitToPage:", fitToPage)
fmt.Println("- autoPageBreaks:", autoPageBreaks)
fmt.Println("- outlineSummaryBelow:", outlineSummaryBelow)
```

Вывод:

```text
Defaults:
- codeName: ""
- enableFormatConditionsCalculation: true
- published: true
- fitToPage: false
- autoPageBreaks: false
- outlineSummaryBelow: true
```

## Вставить столбец {#InsertCol}

```go
func (f *File) InsertCol(sheet, column string) error
```

InsertCol предоставляет функцию для вставки нового столбца перед указателем столбца. Например, создайте новый столбец перед столбцом `C` в `Sheet1`:

```go
err := f.InsertCol("Sheet1", "C")
```

## Вставить строку {#InsertRow}

```go
func (f *File) InsertRow(sheet string, row int) error
```

InsertRow предоставляет функцию для вставки новой строки перед указателем строки. Например, создайте новую строку перед строкой `3` в `Sheet1`:

```go
err := f.InsertRow("Sheet1", 3)
```

## Добавить дубликат строки {#DuplicateRow}

```go
func (f *File) DuplicateRow(sheet string, row int) error
```

DuplicateRow вставляет копию указанной строки ниже указанной, например:

```go
err := f.DuplicateRow("Sheet1", 2)
```

Используйте этот метод с осторожностью, что повлияет на изменения в ссылках, таких как формулы, диаграммы и т. Д. Если на листе есть какое-либо ссылочное значение, это приведет к ошибке файла при его открытии. Excelize лишь частично обновляет эти ссылки в настоящее время.

## Дублирующая строка {#DuplicateRowTo}

```go
func (f *File) DuplicateRowTo(sheet string, row, row2 int) error
```

DuplicateRowTo вставляет копию указанной строки в указанную позицию строки, перемещаясь вниз на существующие строки после целевой позиции, например:

```go
err := f.DuplicateRowTo("Sheet1", 2, 7)
```

Используйте этот метод с осторожностью, что повлияет на изменения в ссылках, таких как формулы, диаграммы и т. Д. Если на листе есть какое-либо ссылочное значение, это приведет к ошибке файла при его открытии. Excelize лишь частично обновляет эти ссылки в настоящее время.

## Создать схему строки {#SetRowOutlineLevel}

```go
func (f *File) SetRowOutlineLevel(sheet string, row int, level uint8) error
```

SetRowOutlineLevel предоставляет функцию для установки уровня уровня строки в одной строке с помощью заданного имени листа и индекса строки. Например, контур 2 строки в `Sheet1` до уровня 1:

<p align="center"><img width="612" src="./images/row_outline_level.png" alt="Создать схему строки"></p>

```go
err := f.SetRowOutlineLevel("Sheet1", 2, 1)
```

## Создать контур столбца {#SetColOutlineLevel}

```go
func (f *File) SetColOutlineLevel(sheet, col string, level uint8) error
```

SetColOutlineLevel предоставляет функцию для установки уровня контуров одного столбца с помощью имени рабочего листа и имени столбца. Например, установите уровень контуров столбца `D` в `Sheet1` равным 2:

<p align="center"><img width="612" src="./images/col_outline_level.png" alt="Создать контур столбца"></p>

```go
err := f.SetColOutlineLevel("Sheet1", "D", 2)
```

## Получить контур линии {#GetRowOutlineLevel}

```go
func (f *File) GetRowOutlineLevel(sheet string, row int) (uint8, error)
```

GetRowOutlineLevel предоставляет функцию, позволяющую получить общий уровень уровня одной строки с помощью заданного имени листа и индекса строки. Например, получите количество строк строки 2 в `Sheet1`:

```go
err := f.GetRowOutlineLevel("Sheet1", 2)
```

## Получить контур колонны {#GetColOutlineLevel}

```go
func (f *File) GetColOutlineLevel(sheet, col string) (uint8, error)
```

GetColOutlineLevel предоставляет функцию для получения уровня контуров одного столбца с указанием имени рабочего листа и имени столбца. Например, получите уровень контуров столбца `D` в `Sheet1`:

```go
level, err := f.GetColOutlineLevel("Sheet1", "D")
```

## Ряд итератора {#Rows}

```go
func (f *File) Rows(sheet string) (*Rows, error)
```

Строки возвращают итератор строк. Например:

```go
rows, err := f.Rows("Sheet1")
if err != nil {
    println(err.Error())
    return
}
for rows.Next() {
    row, err := rows.Columns()
    if err != nil {
        println(err.Error())
    }
    for _, colCell := range row {
        print(colCell, "\t")
    }
    println()
}
```

### Итератор строк - Столбцы

```go
func (rows *Rows) Columns() ([]string, error)
```

Columns возвращают значения столбцов текущей строки.

### Итератор строк - перемещение

```go
func (rows *Rows) Next() bool
```

Next вернется `true`, если найдет следующий элемент строки.

### Итератор строк - обработка ошибок

```go
func (rows *Rows) Error() error
```

Error вернет `error`, когда найдет следующий элемент строки.

## Поиск на листе {#SearchSheet}

```go
func (f *File) SearchSheet(sheet, value string, reg ...bool) ([]string, error)
```

SearchSheet предоставляет функцию для получения координат с помощью заданного имени листа и значения ячейки. Эта функция поддерживает только точное соответствие строк и чисел, не поддерживает вычисляемый результат, отформатированные числа и условный поиск в настоящее время. Если это объединенная ячейка, она вернет координаты верхнего левого угла объединенной области.

Например, найдите координаты значения `100` на `Sheet1`:

```go
result, err := f.SearchSheet("Sheet1", "100")
```

Например, найдите координаты значения в диапазоне `0-9` на листе с именем `Sheet1`:

```go
result, err := f.SearchSheet("Sheet1", "[0-9]", true)
```

## Защитить лист {#ProtectSheet}

```go
func (f *File) ProtectSheet(sheet string, settings *FormatSheetProtection) error
```

ProtectSheet предоставляет функцию предотвращения случайного или преднамеренного изменения других пользователей, перемещения или удаления данных на листе. Например, защитите `Sheet1` с настройками защиты:

<p align="center"><img width="914" src="./images/protect_sheet.png" alt="Защитить лист"></p>

```go
err := f.ProtectSheet("Sheet1", &excelize.FormatSheetProtection{
    Password:      "password",
    EditScenarios: false,
})
```

## Снять защиту листа {#UnprotectSheet}

```go
func (f *File) UnprotectSheet(sheet string) error
```

UnprotectSheet предоставляет функцию для снятия защиты листа Excel.

## Удалить столбец {#RemoveCol}

```go
func (f *File) RemoveCol(sheet, col string) error
```

RemoveCol предоставляет функцию удаления одного столбца по заданному имени рабочего листа и индексу столбца Например, удалите столбец `C` в `Sheet1`:

```go
err := f.RemoveCol("Sheet1", "C")
```

Используйте этот метод с осторожностью, что повлияет на изменения в ссылках, таких как формулы, диаграммы и т. Если на листе есть какое-либо ссылочное значение, это приведет к ошибке файла при его открытии. The excelize только частично обновляет эти ссылки в настоящее время.

## Удалить строку {#RemoveRow}

```go
func (f *File) RemoveRow(sheet string, row int) error
```

RemoveRow предоставляет функцию для удаления одной строки по заданному имени рабочего листа и номеру строки Excel. Например, удалите строку `3` в `Sheet1`:

```go
err := f.RemoveRow("Sheet1", 3)
```

Используйте этот метод с осторожностью, что повлияет на изменения в ссылках, таких как формулы, диаграммы и т. Если на листе есть какое-либо ссылочное значение, это приведет к ошибке файла при его открытии. The excelize только частично обновляет эти ссылки в настоящее время.

## Установить значения строки {#SetSheetRow}

```go
func (f *File) SetSheetRow(sheet, axis string, slice interface{}) error
```

SetSheetRow записывает массив в строку по заданному имени рабочего листа, начальной координате и указателю на тип массива `slice`. Например, запись массива в строку `6` начинается с ячейки `B6` на `Sheet1`:

```go
err := f.SetSheetRow("Sheet1", "B6", &[]interface{}{"1", nil, 2})
```

## Вставить разрыв страницы {#InsertPageBreak}

```go
func (f *File) InsertPageBreak(sheet, cell string) (err error)
```

InsertPageBreak создает разрыв страницы, чтобы определить, где заканчивается напечатанная страница и где начинается следующая страница с заданным именем и осью листа, поэтому содержимое до разрыва страницы будет напечатано на одной странице, а после разрыва страницы - на другой.

## Удалить разрыв страницы {#RemovePageBreak}

```go
func (f *File) RemovePageBreak(sheet, cell string) (err error)
```

RemovePageBreak удаляет разрыв страницы по заданному имени листа и оси.
