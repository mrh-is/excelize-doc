# 차트

## 차트 추가

```go
func (f *File) AddChart(sheet, cell, format string) error
```

AddChart 는 지정된 차트 형식 집합 (예: 오프셋, 축척, 종횡비 설정 및 인쇄 설정) 및 속성 집합을 사용하여 시트에 차트를 추가하는 방법을 제공합니다.

다음은 excelize 에서 지원하는 차트의 `type` 을 보여 주며:

유형|차트
---|---
area                        | 2D 영역 차트
areaStacked                 | 2D 스택 영역 차트
areaPercentStacked          | 2D 100% 스택 영역 차트
area3D                      | 3D 영역 차트
area3DStacked               | 3D 스택 영역 차트
area3DPercentStacked        | 3D 100% 누적 영역 차트
bar                         | 2D 클러스터 막대 차트
barStacked                  | 2D 스택 막대 차트
barPercentStacked           | 2D 100% 스택 막대 차트
bar3DClustered              | 3D 클러스터 막대 차트
bar3DStacked                | 3D 누적 막 대형 차트
bar3DPercentStacked         | 3D 100% 스택 막대 차트
bar3DConeClustered          | 3D 원뿔 클러스터된 막대 차트
bar3DConeStacked            | 3D 원뿔 누적 막대 차트
bar3DConePercentStacked     | 3D 100% 콘 막대 차트
bar3DPyramidClustered       | 3D 피라미드 클러스터 막대 차트
bar3DPyramidStacked         | 3D 피라미드 누적 막대 차트
bar3DPyramidPercentStacked  | 3D 100% 피라미드 누적 막대 차트
bar3DCylinderClustered      | 3D 실린더 클러스터된 막대 차트
bar3DCylinderStacked        | 3D 실린더 스택 막대 차트
bar3DCylinderPercentStacked | 3D 100% 실린더 적층 막대 차트
col                         | 2D 클러스터형 세로 막 대형 차트
colStacked                  | 2D 누적 세로 막 대형 차트
colPercentStacked           | 2D 100% 스택 세로 막 대형 차트
col3DClustered              | 3D 클러스터 된 세로 막 대형 차트
col3D                       | 3D 세로 막 대형 차트
col3DStacked                | 3D 누적 세로 막 대형 차트
col3DPercentStacked         | 3D 100% 누적 세로 막 대형 차트
col3DCone                   | 3D 원뿔 열차트
col3DConeClustered          | 3D 원뿔 클러스터된 열 차트
col3DConeStacked            | 3D 원뿔 누적 열 차트
col3DConePercentStacked     | 3D 100% 콘 스택 열 차트
col3DPyramid                | 3D 피라미드 열차트
col3DPyramidClustered       | 3D 피라미드 클러스터된 열 차트
col3DPyramidStacked         | 3D 피라미드 누적 열 차트
col3DPyramidPercentStacked  | 3D 100% 피라미드 누적 열 차트
col3DCylinder               | 3D 원통 열차트
col3DCylinderClustered      | 3D 실린더 클러스터된 열 차트
col3DCylinderStacked        | 3D 실린더 스택 컬럼 차트
col3DCylinderPercentStacked | 3D 100% 실린더 스택 컬럼 차트
doughnut                    | 도넛 차트
line                        | 꺾은 선형 차트
pie                         | 원형 차트
pie3D                       | 3D 원형 차트
radar                       | 레이더 차트
scatter                     | 분산 형 차트
surface3D                   | 3D 표면 차트
wireframeSurface3D          | 3D 와이어프레임 표면 차트
contour                     | 등고선 차트
wireframeContour            | 와이어프레임 윤곽 차트
bubble                      | 버블 차트
bubble3D                    | 3D 버블 차트

Office Excel 차트 데이터 영역 `series` 에서 데이터를 그릴 정보 집합, 범례 항목 (계열) 및 가로 (범주) 축 레이블을 지정합니다.

설정할 수 있는 `series` 옵션은 다음과 같습니다:

매개 변수|설명
---|---
name|범례 항목 (계열) 은 차트 범례 및 수식 표시줄에 표시됩니다. `name` 매개 변수는 선택 사항입니다. 이 값을 지정하지 않으면 기본값은 `Series 1 .. n`. 수식 표현에 대한 `name` 지원(예: `Sheet1!$A$1`).
categories|Horizontal (category) axis label. The `categories` parameter is optional in most chart types, the default is a contiguous sequence of the form `1..n`.
수평(범주) 축 레이블입니다. '범주' 매개 변수는 대부분의 차트 유형에서 선택 사항이며 기본값은 '1..n' 형식의 연속 시퀀스입니다.
values|`series` 에서 가장 중요한 매개 변수인 차트 데이터 영역도 차트를 만들 때 필요한 유일한 매개 변수입니다. 이 옵션은 차트를 차트가 표시하는 워크시트 데이터에 연결합니다.

차트 범례의 속성을 설정합니다. 설정할 수 있는 옵션은 다음과 같습니다:

매개 변수|유형|설명
---|---|---
position|string|차트 범례의 위치
show_legend_key|bool|범례 표시하지만 차트와 겹치지 않음

차트 범례의 `position` 를 설정합니다. 기본 범례 위치는 `right` 입니다. 사용 가능한 위치는 다음과 같습니다.

매개 변수|설명
---|---
top|On top
bottom|On bottom
left|On left
right|On right
top_right|On top right

범례 키를 설정하는 `show_legend_key` 매개 변수는 데이터 레이블에 표시됩니다. 기본값은 `false` 입니다.

차트 제목은 `title` 개체의 `name` 매개변수를 선택하여 설정되며 제목은 차트 위에 표시됩니다. 매개 변수 `name` 은 아이콘 제목을 지정하지 않으면 `Sheet1!$A$1` 과 같은 수식 표현의 사용을 지원합니다.

`show_blanks_as` 매개변수는 "셀 숨기기 및 빈 셀" 설정을 제공합니다. 기본값은 `gap` 입니다. Excel 응용 프로그램에서 "빈 셀은" 로 표시됩니다: "space". 다음은 이 매개 변수에 대한 선택적 값입니다.

매개 변수|설명
---|---
gap|space
span|Connect data points with straight lines
zero|zero value

매개변수 `format` 은 차트 오프셋, 배율, 종횡비 설정 및 인쇄 특성과 [`AddPicture()`](image.md#AddPicture) 함수에 사용되는 매개 변수에 대한 설정을 제공합니다.

차트 플롯 영역의 위치를 플롯 영역별로 설정합니다. 설정할 수 있는 속성은 다음과 같습니다:

매개 변수|유형|기본값|설명
---|---|---|---
show_bubble_size|bool|`false`|거품 크기를 지정하여 데이터 레이블에 표시해야 합니다.
show_cat_name|bool|`true`|범주 이름
show_leader_lines|bool|`false`|범주 이름이 데이터 레이블에 표시되도록 지정합니다.
show_percent|bool|`false`|백분율이 데이터 레이블에 표시되도록 지정합니다.
show_series_name|bool|`false`|계열 이름이 데이터 레이블에 표시되도록 지정합니다.
show_val|bool|`false`|값이 데이터 레이블에 표시되도록 지정합니다.

기본 수평 및 세로 축 옵션을 `x_axis` 및 `y_axis` 으로 설정합니다. 설정할 수 있는 속성은 다음과 같습니다:

매개 변수|유형|기본값|설명
---|---|---|---
reverse_order|bool|`false`|역순 (차트 방향) 의 범주 또는 값을 지정합니다. `reverse_order` 속성은 선택 사항입니다.
maximum|int|`0`|고정 최대값 0 이 자동임을 지정합니다. 최대 속성은 선택 사항입니다.
minimum|int|`0`| 고정 된 최소, 0 은 자동 지정 합니다. 최소 속성은 선택 사항입니다. 기본값은 자동입니다.

차트 크기를 `dimension` 속성으로 설정합니다. 차원 속성은 선택 사항입니다. 설정할 수 있는 속성은 다음과 같습니다:

매개 변수|유형|기본값|설명
---|---|---|---
height|int|290|높이
width|int|480|너비

### 2D 영역 차트 {#area}

예를 들어 다음과 같은 2D 영역 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/2d_area_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 2D 영역 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"bar","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"left","show_legend_key":false},"title":{"name":"Fruit 2D Clustered Bar Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 2D 스택 영역 차트 {#areaStacked}

예를 들어 다음과 같은 2D 스택 영역 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/2d_stacked_area_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 2D 스택 영역 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"areaStacked","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"bottom","show_legend_key":false},"title":{"name":"Fruit 2D Stacked Area Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 2D 100% 스택 영역 차트 {#areaPercentStacked}

### 3D 영역 차트 {#area3D}

예를 들어 다음과 같은 3D 영역 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/3d_area_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 3D 영역 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 7, "C2": 7, "D2": 8, "B3": 5, "C3": 4, "D3": 4, "B4": 2, "C4": 3, "D4": 3}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"area3D","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"bottom","show_legend_key":false},"title":{"name":"Fruit 3D Area Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 3D 스택 영역 차트 {#area3DStacked}

예를 들어 다음과 같은 3D 스택 영역 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/3d_stacked_area_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 3D 스택 영역 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"area3DStacked","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"bottom","show_legend_key":false},"title":{"name":"Fruit 3D Stacked Area Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 3D 100% 누적 영역 차트 {#area3DPercentStacked}

예를 들어 다음과 같은 3D 100% 누적 영역 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/3d_percent_stacked_area_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 3D 100% 누적 영역 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"area3DPercentStacked","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"bottom","show_legend_key":false},"title":{"name":"Fruit 3D 100% Stacked Area Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 2D 클러스터 막대 차트 {#bar}

예를 들어 다음과 같은 2D 클러스터 막대 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/2d_clustered_bar_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 2D 클러스터 막대 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"bar","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"left","show_legend_key":false},"title":{"name":"Fruit 2D Clustered Bar Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 2D 스택 막대 차트 {#barStacked}

예를 들어 다음과 같은 2D 스택 막대 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/2d_stacked_bar_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 2D 스택 막대 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"barStacked","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"left","show_legend_key":false},"title":{"name":"Fruit 2D Stacked Bar Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 2D 100% 스택 막대 차트 {#barPercentStacked}

예를 들어 다음과 같은 2D 100% 스택 막대 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/2d_percent_stacked_bar_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 2D 100% 스택 막대 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"barPercentStacked","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"left","show_legend_key":false},"title":{"name":"Fruit 2D Stacked 100% Bar Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 3D 클러스터 막대 차트 {#bar3DClustered}

예를 들어 다음과 같은 3D 클러스터 막대 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/3d_clustered_bar_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 3D 클러스터 막대 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"bar3DClustered","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"left","show_legend_key":false},"title":{"name":"Fruit 3D Clustered Bar Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 3D 누적 막 대형 차트 {#bar3DStacked}

예를 들어 다음과 같은 3D 누적 막 대형 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/3d_stacked_bar_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 3D 누적 막 대형 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"bar3DStacked","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"left","show_legend_key":false},"title":{"name":"Fruit 3D Stacked Bar Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 3D 100% 스택 막대 차트 {#bar3DPercentStacked}

예를 들어 다음과 같은 3D 100% 스택 막대 차트 를 추가합니다:

<p align="center"><img width="769" src="./images/3d_percent_stacked_bar_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 3D 100% 스택 막대 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"bar3DPercentStacked","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"left","show_legend_key":false},"title":{"name":"Fruit 3D 100% Stacked Bar Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 3D 원뿔 클러스터된 막대 차트 {#bar3DConeClustered}

### 3D 원뿔 누적 막대 차트 {#bar3DConeStacked}

### 3D 100% 콘 막대 차트 {#bar3DConePercentStacked}

### 3D 피라미드 클러스터 막대 차트 {#bar3DPyramidClustered}

### 3D 피라미드 누적 막대 차트 {#bar3DPyramidStacked}

### 3D 100% 피라미드 누적 막대 차트 {#bar3DPyramidPercentStacked}

### 3D 실린더 클러스터된 막대 차트 {#bar3DCylinderClustered}

### 3D 실린더 스택 막대 차트 {#bar3DCylinderStacked}

### 3D 100% 실린더 적층 막대 차트 {#bar3DCylinderPercentStacked}

### 2D 클러스터형 세로 막 대형 차트 {#col}

예를 들어 다음과 같은 2D 클러스터형 세로 막 대형 차트 를 추가합니다:

<p align="center"><img width="769" src="./images/2d_clustered_column_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 2D 클러스터형 세로 막 대형 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"col","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"left","show_legend_key":false},"title":{"name":"Fruit 2D Column Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 2D 누적 세로 막 대형 차트 {#colStacked}

### 2D 100% 스택 세로 막 대형 차트 {#colPercentStacked}

### 3D 클러스터 된 세로 막 대형 차트 {#col3DClustered}

예를 들어 다음과 같은 3D 클러스터 된 세로 막 대형 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/3d_clustered_column_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 3D 클러스터 된 세로 막 대형 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"col3DClustered","series":[{"name":"Sheet1!$A$2","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"bottom","show_legend_key":false},"title":{"name":"Fruit 3D Clustered Column Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero","x_axis":{"reverse_order":true},"y_axis":{"maximum":7.5,"minimum":0.5}}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 3D 세로 막 대형 차트 {#col3D}

### 3D 누적 세로 막 대형 차트 {#col3DStacked}

### 3D 100% 누적 세로 막 대형 차트 {#col3DPercentStacked}

### 3D 원뿔 열차트 {#col3DCone}

### 3D 원뿔 클러스터된 열 차트 {#col3DConeClustered}

### 3D 원뿔 누적 열 차트 {#col3DConeStacked}

### 3D 100% 콘 스택 열 차트 {#col3DConePercentStacked}

### 3D 피라미드 열차트 {#col3DPyramid}

### 3D 피라미드 클러스터된 열 차트 {#col3DPyramidClustered}

### 3D 피라미드 누적 열 차트 {#col3DPyramidStacked}

### 3D 100% 피라미드 누적 열 차트 {#col3DPyramidPercentStacked}

### 3D 원통 열차트 {#col3DCylinder}

### 3D 실린더 클러스터된 열 차트 {#col3DCylinderClustered}

### 3D 실린더 스택 컬럼 차트 {#col3DCylinderStacked}

### 3D 100% 실린더 스택 컬럼 차트 {#col3DCylinderPercentStacked}

### 도넛 차트 {#doughnut}

예를 들어 다음과 같은 도넛 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/doughnut_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 도넛 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A1": "Apple", "B1": "Orange", "C1": "Pear"}
    values := map[string]int{"A2": 2, "B2": 3, "C2": 3}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"doughnut","series":[{"name":"Sheet1!$A$2","categories":"Sheet1!$A$1:$C$1","values":"Sheet1!$A$2:$C$2"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"right","show_legend_key":false},"title":{"name":"Fruit Doughnut Chart"},"plotarea":{"show_bubble_size":false,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":false,"show_val":false},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 꺾은 선형 차트 {#line}

예를 들어 다음과 같은 꺾은 선형 차트 를 추가합니다:

<p align="center"><img width="769" src="./images/line_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 꺾은 선형 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }

    f.AddChart("Sheet1", "E1", `{"type":"line","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"top","show_legend_key":false},"title":{"name":"Fruit Line Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    // 통합 문서 저장
    err := f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 원형 차트 {#pie}

예를 들어 다음과 같은 원형 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/pie_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 원형 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }

    f.AddChart("Sheet1", "E1", `{"type":"pie","series":[{"name":"Sheet1!$A$2","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$2:$D$2"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"bottom","show_legend_key":false},"title":{"name":"Fruit Pie Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":false,"show_val":false},"show_blanks_as":"gap"}`)
    // 통합 문서 저장
    err := f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 3D 원형 차트 {#pie3D}

예를 들어 다음과 같은 3D 원형 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/3d_pie_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 3D 원형 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }

    f.AddChart("Sheet1", "E1", `{"type":"pie3D","series":[{"name":"Sheet1!$A$2","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$2:$D$2"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"bottom","show_legend_key":false},"title":{"name":"Fruit 3D Pie Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":false,"show_val":false},"show_blanks_as":"zero"}`)
    // 통합 문서 저장
    err := f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 레이더 차트 {#radar}

예를 들어 다음과 같은 레이더 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/radar_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 레이더 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"radar","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"top","show_legend_key":false},"title":{"name":"Fruit Radar Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":false,"show_val":false},"show_blanks_as":"span"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 분산 형 차트 {#scatter}

예를 들어 다음과 같은 분산 형 차트 를 추가합니다:

<p align="center"><img width="770" src="./images/scatter_chart.png" alt="Go 언어를 사용하여 엑셀리즈로 분산 형 차트 만들기"></p>

```go
package main

import (
    "fmt"

    "github.com/360EntSecGroup-Skylar/excelize"
)

func main() {
    categories := map[string]string{"A2": "Small", "A3": "Normal", "A4": "Large", "B1": "Apple", "C1": "Orange", "D1": "Pear"}
    values := map[string]int{"B2": 2, "C2": 3, "D2": 3, "B3": 5, "C3": 2, "D3": 4, "B4": 6, "C4": 7, "D4": 8}
    f := excelize.NewFile()
    for k, v := range categories {
        f.SetCellValue("Sheet1", k, v)
    }
    for k, v := range values {
        f.SetCellValue("Sheet1", k, v)
    }
    err := f.AddChart("Sheet1", "E1", `{"type":"scatter","series":[{"name":"Sheet1!$A$2","categories":"","values":"Sheet1!$B$2:$D$2"},{"name":"Sheet1!$A$3","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$3:$D$3"},{"name":"Sheet1!$A$4","categories":"Sheet1!$B$1:$D$1","values":"Sheet1!$B$4:$D$4"}],"format":{"x_scale":1.0,"y_scale":1.0,"x_offset":15,"y_offset":10,"print_obj":true,"lock_aspect_ratio":false,"locked":false},"legend":{"position":"left","show_legend_key":false},"title":{"name":"Fruit Scatter Chart"},"plotarea":{"show_bubble_size":true,"show_cat_name":false,"show_leader_lines":false,"show_percent":true,"show_series_name":true,"show_val":true},"show_blanks_as":"zero"}`)
    if err != nil {
        fmt.Println(err)
    }
    // 통합 문서 저장
    err = f.SaveAs("./Book1.xlsx")
    if err != nil {
        fmt.Println(err)
    }
}
```

### 3D 표면 차트 {#surface3D}

### 3D 와이어프레임 표면 차트 {#wireframeSurface3D}

### 등고선 차트 {#contour}

### 와이어프레임 윤곽 차트 {#wireframeContour}

### 버블 차트 {#bubble}

### 3D 버블 차트 {#bubble3D}