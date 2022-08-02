---
layout: post
title: (swift) BASIC_11. Alamofire
description: "(swift) Alamofire"
tags: [swift, basic, 공부]
comments: true
---

> # [swift] BASIC_11. Alamofire

<br>

# Alamofire

## Alamofire란
Swift 기반의 HTTP 네트워킹 라이브러리이다.
URLSession에 기반한 라이브러리로, 네트워킹 작업을 단순화하고, 네트워킹을 위한 다양한 메서드와 JSON 파싱을 제공한다.

<br>
<br>

## Alamofire 특성
 - 연결가능한 Request, Response 메서드를 제공한다.
 - URL JSON형태의 파라미터 인코딩을 지원한다.
 - 파일 데이터 스트링 멀티파트폼 데이터 등 업로드 기능을 제공한다.
 - HTTP Response 검증을 제공한다.
 - 광범위한 단위 테스트 및 통합 테스트를 보장한다.

<br>
<br>

## URLSession 대신 Alamofire를 사용하는 이유
 - 코드의 간소화, 가독성 측면에서 도움을 준다.  
 - 여러 기능을 직접 구축하지 않아도 쉽게 사용할 수 있다.

<br>

다음은 URLSession 코드이다.
``` swift
// 호출 URL 만들기
var components = URLComponents(string: "https://api~~~~~~~~")!
components.queryItems = ["title": "Junhyeok"].map { (key, value) in
  URLQueryItem(name: key, value: value)
}

// Request 생성 및 실행
let request = try! URLRequest(url: components.url!, method: .get)
URLSession.shared.dataTask(with: request) { (data, response, error) in 
  do {
    guard let data = data,
      let response = response as? HTTPURLResponse, (200 ..< 300) ~= response.statusCode, error == nil
      else {
        throw error ?? Error.requestFailed
    }
    let response = try JSONDecoder().decode(Response.self, from: data)
    print("Success \(response)")
  } catch {
    print("Failure: \(error.localizedDescription)")
  }
}
```

<br>

이를 Alamofire를 이용하면 다음과 같이 간소화하여 가독성을 높일 수 있다.  
``` swift
AF.request("https://api~~~~~~~~~~", method: .get, parameters: ["title": "Junhyeok"])
  .validate()
  .responseJSON { response in
    switch response.result {
    case .success(let result):
      debugPrint("success \(result)")
    case .failure(let error):
      debugPrint("Failure \(error)")
    }
  }
```

<br>
<br>
<br>

# Alamofire Request

``` swift
// 파라미터로 URL과 HTTP 메서드 등을 쉽게 설정할 수 있다.
open func request<Parameters: Encodable>(_ convertible: URLConvertible,
                                         method: HTTPMethod = .get,
                                         parameters: Parameters? = nil,
                                         encoder: ParameterEncoder = URLEncodedFormParameterEncoder.default,
                                         headers: HTTPHeaders? = nil,
                                         interceptor: RequestInterceptor? = nil) -> DataRequest
```

<br>
<br>
<br>

# Alamofire HTTP Method

``` swift
public struct HTTPMethod: RawRepresentable, Equatable, Hashable {
  public static let connect = HTTPMethod(rawValue: "CONNECT")
  public static let delete = HTTPMethod(rawValue: "DELETE")
  public static let get = HTTPMethod(rawValue: "GET")
  public static let head = HTTPMethod(rawValue: "HEAD")
  public static let options = HTTPMethod(rawValue: "OPTIONS")
  public static let patch = HTTPMethod(rawValue: "PATCH")
  public static let post = HTTPMethod(rawValue: "POST")
  public static let put = HTTPMethod(rawValue: "PUT")
  public static let trace = HTTPMethod(rawValue: "TRACE")

  public let rawValue: String

  public init(rawValue: String) {
    self.rawValue = rawValue
  }
}
```

<br>

``` swift
AF.request("https://httpbin.org/get")
AF.request("https://httpbin.org/post", method: .post)
AF.request("https://httpbin.org/put", method: .put)
AF.request("https://httpbin.org/delete", method: .delete)
```

<br>
<br>
<br>

# Alamofire Response
``` swift
// Response Handler - Unserialized Response
func response(queue: DispatchQueue = .main,
              completionHandler: @escaping (AFDataResponse<Data?>) -> Void) -> Self

// Response Serializer Hander - Serialize using the passed Serializer
func response<Serializer: DataResponseSerializerProtocol>(queue: DispatchQueue = .main,
                                                          responseSerializer: Serializer,
                                                          completionHandler: @escapting (AFDataResponse<Serializer.SerializedObject>) -> Void) -> Self

//Response Data Handler - Serialized into Data
func responseData(queue: DispatchQueue = .main,
                  dataPreprocessor: DataPreprocessor = DataResponseSerializer.defaultDataPreprocessor,
                  emptyResponseCodes: Set<Int> = DataResponseSerializer.defaultEmptyResponseCodes,
                  emptyRequestMethods: Set<HTTPMethod> = DataResponseSerializer.defaultEmptyRequestMethods,
                  completionHandler: @escaping (AFDataResponse<Data>) -> Void) -> Self

// Response String Handler - Serialized into String
func responseString(queue: DispatchQueue = .main,
                    dataPreprocessor: Datapreprocessor = StringResponseSerializer.defaultDataPreprocessor,
                    encoding: String.Encoding? = nil,
                    emptyResponseCodes: Set<Int> = StringResponseSerializer.defaultEmptyResponseCodes,
                    emptyRequestMethods: Set<HTTPMethod> = StringResponseSerializer.defaultEmptyRequestMethods,
                    completionHandler: @escaping (AFDataResponse<String>) -> Void) -> Self

// Response JSON Handler - Serialized into Any Using JSONSerialization
func responseJSON(queue: DispatchQueue = .main,
                  dataPreprocessor: DataPreprocessor = JSONResponseSerializer.defaultDataPreprocessor,
                  emptyResponseCodes: Set<Int> = JSONResponseSerializer.defaultEmptyResponseCodes,
                  emptyRequestMEthods: Set<HTTPMethod> = JSONResponseSerializer.defaultEmptyRequestMethods,
                  options: JSONSerialization.ReadingOptions = .allowFragments,
                  completionHandler: @escaping (AFDataResponse<Any>) -> Void) -> Self

// Response Decodable Handler - Serialized into Decodable Type
func responseDecodable<T: Decodable>(of type: T.Type = T.self,
                                     queue: DispatchQueue = .main,
                                     dataPreprocessor: DataPreprocessor = DecodableResponseSerializer<T>.defaultDataPreprocessor,
                                     decoder: DataDecoder = JSONDecoder(),
                                     emptyResponseCodes: Set<Int> = DecodableResponseSerializer<T>.defaultEmptyResponseCodes,
                                     emptyRequestMethods: Set<HTTPMethod> = DecodableResponseSerializer<T>.defaultEmptyRequestMethods,
                                     completionHandler: @escaping (AFDataResponse<T>) -> Void) -> Self
```

<br>
<br>

다음과 같이 사용한다.  
``` swift
AF.request("https://httpbin.org/get").responseJSON { response in
  debugPrint(response)
}
```