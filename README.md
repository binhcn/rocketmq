# **`Apache RocketMQ`**

## Overview

- Apache RocketMQ là một platform messaging và streaming phân tán với những đặc trưng: low-latency, hiệu năng cao và độ tin cậy, sức chứa lên đến trillion-level và linh hoạt trong việc scale.

  <img src ="media/components.png" width="70%"/>

- gồm 4 thành phần và tất cả chúng đều có thể tổ chức thành cluster cũng như dễ dàng scale theo chiều ngang:

  - NameServer 2 feature chính:
    - Quản lý broker: chấp nhận đăng ký từ cụm broker và hỗ trợ cơ cấu heartbeat để check broker có còn sống hay không.
    - Quản lý routing: mỗi NameServer sẽ giữ toàn bộ routing info về broker cluster và queue info để client query.
  - Broker server gồm sub-module quan trọng:
    - Remoting module: broker entry, handle requests từ clients
    - Client manager: quản lý clients và duy trì topic subscription trên consumer
    - Store service: cung cấp các API đơn giản để lưu trữ và query message ở physical disk
    - HA service: hỗ trợ đồng bộ dữ liệu giữa master và slace broker
    - Index service: đánh index messages theo key và tăng tốc query

    <img src ="media/broker-features.png" width="70%"/>

  - Producer
  - Consumer