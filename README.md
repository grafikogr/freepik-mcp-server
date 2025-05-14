[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/grafikogr-freepik-mcp-server-badge.png)](https://mseep.ai/app/grafikogr-freepik-mcp-server)

# Freepik Flux AI MCP Sunucusu

Bu proje, Claude Desktop için Freepik'in Flux AI görsel üretme hizmetini kullanarak metin açıklamalarından görseller oluşturan bir Model Context Protocol (MCP) sunucusudur.

## Özellikler

- Metin açıklamalarından görsel oluşturma
- Çeşitli en-boy oranı seçenekleri
- Tarayıcıda otomatik görsel açma
- Sağlam hata yönetimi ve yeniden deneme mekanizması

## Gereksinimler

- Node.js 20.x veya üstü
- Freepik API anahtarı (https://www.freepik.com/developers/dashboard/api-key adresinden alınabilir)

## Kurulum

1. Bu depoyu klonlayın veya indirin:
```bash
git clone https://github.com/grafikogr/freepik-mcp-server.git
cd freepik-mcp-server
```

2. Bağımlılıkları yükleyin:
```bash
npm install
```

3. `.env.example` dosyasını `.env` olarak kopyalayın ve Freepik API anahtarınızı ekleyin:
```bash
cp .env.example .env
```

4. `.env` dosyasını düzenleyin ve `FREEPIK_API_KEY` değişkenini kendi API anahtarınızla değiştirin.

## Kullanım

1. Sunucuyu başlatın:
```bash
npm start
```

2. Claude Desktop uygulamanızda bu sunucuyu aşağıdaki komutla çalıştırın:
```
@freepik help
```

## Claude Desktop Entegrasyonu

Claude Desktop'ta MCP sunucusunu yapılandırmak için şu adımları izleyin:

1. Claude Desktop ayarlarına gidin.
2. `mcpServers` bölümüne şu yapılandırmayı ekleyin:
```json
"mcpServers": {
  "freepik": {
    "command": "node",
    "args": ["indirdiğiniz/konum/freepik-mcp-server/index.js"]
  }
}
```
3. Claude Desktop'u yeniden başlatın.

## Araçlar

### generate_image

Metin açıklaması ve görsel oranı (isteğe bağlı) ile görsel oluşturur.

**Parametreler:**
- `prompt`: Görsel için metin açıklaması (zorunlu)
- `aspect_ratio`: Görsel oranı (isteğe bağlı)

**Kullanılabilir Görsel Oranları:**
- `square_1_1`: Kare (1:1)
- `classic_4_3`: Klasik (4:3)
- `traditional_3_4`: Geleneksel (3:4)
- `widescreen_16_9`: Geniş ekran (16:9)
- `social_story_9_16`: Sosyal medya hikayesi (9:16)
- `standard_3_2`: Standart (3:2)
- `portrait_2_3`: Portre (2:3)
- `horizontal_2_1`: Yatay (2:1)
- `vertical_1_2`: Dikey (1:2)
- `social_post_4_5`: Sosyal medya gönderisi (4:5)

## Konfigürasyon

`.env` dosyasında aşağıdaki ayarları yapılandırabilirsiniz:

- `FREEPIK_API_KEY`: Freepik API anahtarınız (zorunlu)
- `REQUEST_TIMEOUT`: İstek zaman aşımı süresi (milisaniye, varsayılan: 30000)
- `RETRY_ATTEMPTS`: Başarısız isteklerin yeniden deneme sayısı (varsayılan: 3)

## Örnekler

1. Basit bir görsel oluşturma:
   ```
   @freepik Bana bir kedi görseli oluştur
   ```

2. Belirli bir en-boy oranıyla görsel oluşturma:
   ```
   @freepik Bana widescreen_16_9 oranında dağ manzarası oluştur
   ```

## Sorun Giderme

- API anahtarı sorunları için `.env` dosyasını kontrol edin ve Freepik API anahtarınızın doğru olduğundan emin olun.
- Ağ bağlantı sorunları için internet bağlantınızı kontrol edin.
- Sunucu çalışma sorunları için Node.js sürümünüzün 20.x veya üstü olduğundan emin olun.
- Daha fazla hata ayıklama bilgisi için konsol çıktısını kontrol edin.

## Lisans

Bu proje MIT lisansı altında lisanslanmıştır.