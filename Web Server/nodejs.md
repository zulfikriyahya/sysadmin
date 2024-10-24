# Instalasi Node.js

## Instalasi Via nvm (Node Version Manager)

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
```

### Download dan instal Node.js (mungkin perlu restart terminal)

```
nvm install 20
```

### Memverifikasi versi Node.js yang tepat di lingkungan

```
node -v
```

### Memverifikasi versi npm yang tepat di lingkungan

```
npm -v
```

## Instalasi Via fnm (Fast Node Manager)

```
curl -fsSL https://fnm.vercel.app/install | bash
```

### Aktivasi fnm

```
source ~/.bashrc
```

### Download dan instal Node.js

```
fnm use --install-if-missing 20
```

### Memverifikasi versi Node.js yang tepat di lingkungan

```
node -v
```

### Memverifikasi versi npm yang tepat di lingkungan

```
npm -v
```
