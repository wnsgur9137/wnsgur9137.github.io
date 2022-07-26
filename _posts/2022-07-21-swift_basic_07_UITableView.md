---
layout: post
title: (swift) BASIC_07. UITableView
description: "(swift) 테이블 뷰"
tags: [swift, basic, 공부]
comments: true
---

> # [swift] BASIC_07. UITableView

<br>

# UITableView

데이터들을 목록 형태로 보여줄 수 있는 가장 기본적인 UI 컴포넌트  
또한 UIScrollView를 상속해 스크롤을 통해 리스트 형태로 많은 정보를 보여줄 수 있다.  
 - 여러 개의 Cell을 가지고 이고 하나의 열과 여러 줄의 행을 지니고 있으며, 수직으로만 스크롤 가능하다.
 - 섹션을 이용해 행을 그룹화하여 컨텐츠를 좀 더 쉽게 탐색할 수 있다.
 - 섹션의 헤더와 푸터에 View를 구성하여 추가적인 정보를 표시할 수 있다.

<br>
<br>

## Delegate
 - TableView의 동작과 외관을 담당한다.

<br>
<br>

## DataSource
 - Data를 받아 View를 보여주는 담당

<br>
<br>
<br>

# UITableViewDataSource
 - UITableViewDataSource는 테이블 뷰를 생성하고 수정하는데 필요한 정보를 테이블 뷰 객체에 제공

``` swift
public protocol UITableViewDataSource: NSObjectProtocol {
    
    // 각 세션에 표시할 행의 개수를 묻는 메서드
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int

    // 특정 인덱스 Row의 Cell에 대한 정보를 넣어 Cell을 반환하는 메서드
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell

    // 총 섹션 개수를 묻는 메서드
    optional func numberOfSections(in tableView: UITableView) -> Int

    // 특정 섹션의 헤더 타이틀을 묻는 메서드
    optional func tableView(_ tableView: UITableView, titleForHeaderInSection section: Int) -> String?

    // 특정 세션의 풋터 타이틀을 묻는 메서드
    optional func tableView(_ tableView: UITableView, titleForFooterInSection section: Int) -> String?

    // 특정 위치의 행이 편집 가능한지 묻는 메서드
    optional func tableView(_ tableView: UITableView, canEditRowAt indexPath: IndexPath) -> Bool
    
    // 특정 위치의 행을 재정렬 할 수 있는지 묻는 메서드
    optional func tableView(_ tableView: UITableView, canMoveRowAt indexPath: IndexPath) -> Bool

    // 테이블 뷰 섹션 인덱스 타이틀을 묻는 메서드
    optional func sectionIndexTitles(for tableView: UITableView) -> [String]?

    // 인덱스에 해당하는 섹션을 알려주는 메서드
    optional func tableView(_ tableView: UITableView, sectionForSectionIndexTitle title: String, at index: Int) -> Int

    // 스와이프 모드, 편집 모드에서 버튼을 선택하면 호출 되는 메서드
    // 해당 메서드에서는 행에 변경사항을 Commit 해야 함
    optional func tableView(_ tableView: UITableView, commit editingStyle: UITableViewCell.EditingStle, forRowAt indexPath: IndexPath)

    // 행이 다른 위치로 이동되면 어디에서 어디로 이동했는지 알려주는 메서드
    optional func tableView(_ tableView: UITableView, moveRowAt sourceIndexPath: IndexPath, to destinationIndexPath: IndexPath)
}
```
<br>
<br>
<br>

# UITableViewDelegate
 - UITableViewDelegate는 테이블 뷰의 시각적인 부분을 설정하고, 행의 액션 관리, 엑세서리 뷰 지원, 그리고 테이블 뷰의 개별 행 편집을 도와준다.


``` swift
public protocol UITableViewDelegate: UiScrollViewDelegate {

    // 행이 선택되었을 때 호출되는 메서드
    optional func tableView(_ tableView: UITableview, didSelectRowAt indexPath: IndexPath)

    // 행이 선택 해제되었을 때 호출되는 메서드
    optional func tableView(_ tableView: UITableview, didDeselectRowAt indexPath: IndexPath)

    // 특정 위치 행의 높이를 묻는 메서드
    optional func tableView(_ tableView: UITableview, heightForRowAt indexPath: IndePath) -> CGFloat

    // 지정된 섹션의 헤더뷰 또는 푸터뷰에 표시할 View가 어떤 것인지 묻는 메서드
    optional func tableView(_ tableView: UITableview, viewForHeaderInSection section: Int) -> UIView?
    optional func tableView(_ tableView: UITableview, viewForFooterInSection section: Int) -> UIView?

    // 지정된 섹션의 헤더뷰 또는 푸터뷰의 높이를 묻는 메서드
    optional func tableView(_ tableView: UITableview, heightForHeaderInSection section: Int) -> CGFloat
    optional func tableView(_ tableView: UITableview, heightForFooterInSection section: Int) -> CGFloat

    // 테이블 뷰가 편집 모드에 들어갔을 때 호출되는 메서드
    optional func tableView(_ tableView: UITableview, willBeginEditingRowAt indexPath: IndexPath)

    // 테이블 뷰가 편집 모드에서 빠져나왔을 때 호출되는 메서드
    optional func tableView(_ tableView: UITableview, didEndEditingRowAt indexPath: IndexPath?)

    // 테이블 뷰가 셀을 사용하여 행을 그리기 직전에 호출되는 메서드
    optional func tableView(_ tableView: UITableview, willDisplay cell: UITableViewCell, forRowAt indexPath: IndexPath)

    // 텡븗 ㅠ로부터 셀이 화면에 사라지면 호출되는 메서드
    optional func tableView(_ tableView: UITableview, didEndDisplaying cell: UITableViewCell, forRowAt indexPath: IndexPath)
}
```