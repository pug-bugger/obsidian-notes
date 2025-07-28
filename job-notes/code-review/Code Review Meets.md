
Dirbant su huge arrays reiktų naudoti `new Int8Array([-128, 128])` 1-bit or `new Int16Array([-32_768, 32_768])` 2-bit or `new Uint32Array([0, 4_294_967_295])` 4-bit. Arba Float16Array ir Float64Array.
Kiekvienas kintamas užima 8 bitus, o čia nuo 1 iki 4.