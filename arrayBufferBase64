 
 userAvatars: { [key: number]: string } = {};
 
 arrayBufferToBase64(buffer: ArrayBuffer){
    let binary = '';
    const bytes = new Uint8Array(buffer)
    const len = bytes.byteLength;

    for (let i=0; i<len; i++){
      binary += String.fromCharCode(bytes[i])
    }

    return window.btoa(binary)

 }

async getAvatar(userId: number): Promise<void>{
    try {
      const response$ = this.http.get(`url/${userId}`, { responseType: 'arraybuffer' });
      const response = await firstValueFrom(response$)  // to Promise is deprecated
      const base64Data = this.arrayBufferToBase64(response)
      const avatarUrl = 'data:image/png;base64,' + base64Data;
      this.userAvatars[userId] = avatarUrl;
    }
    catch(error){
      console.log('Error fetching avatar for user ID:', userId, error);
    }  
  }
  
  <img [src]="userAvatars[user.id]" alt="">
