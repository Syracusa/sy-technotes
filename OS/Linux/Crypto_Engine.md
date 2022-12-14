# Linux Crypto Engine API


## include/linux/crypto.h
### struct crypto_alg

## include/crypto/akcipher.h

## include/crypto/kpp.h
key-agreement protocol primitives


## crypto/algapi.c
### crypto_register_alg()
+ int crypto_register_alg(struct crypto_alg *alg)


## crypto/kpp.c
+ int crypto_register_kpp(struct kpp_alg *alg)

# Examples
## crypto/ecdh.c




# OpenSSL AF_ALG
Note : Openssl 'engine' API has deprecated.

```
afalg_ciphers() 
OPENSSL_init_crypto() -> ossl_init_engine_dynamic() -> engine_load_dynamic_int() -> engine_dynamic() -> dynamic_ctrl() -> dynamic_load() -> bind_engine() -> bind_helper() -> bind_afalg() -> afalg_aes_cbc() -> afalg_cipher_init() -> afalg_create_sk()


EVP_Cipher() -> do_cipher() -> afalg_do_cipher() -> afalg_start_cipher_sk()

```

## engines/e_afalg.c

### afalg_ciphers()

### afalg_aes_cbc()
static const EVP_CIPHER *afalg_aes_cbc(int nid)

### afalg_cipher_init()
static int afalg_cipher_init(EVP_CIPHER_CTX *ctx, const unsigned char *key,
                             const unsigned char *iv, int enc)

### afalg_create_sk()
static int afalg_create_sk(afalg_ctx *actx, const char *ciphertype,
                                const char *ciphername)