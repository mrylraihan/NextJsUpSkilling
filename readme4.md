test pc
app.js

const validateIp = (input)=>{
    if(!input){
        return 
    }
    // let result = ''
    let ipArr = input.split('.')
    if(ipArr.length<=3){
        return 'There are 4 parts to a valid IP Address'
    }

    if(ipArr.includes("")){
        return 'a valid IP has 4 numerical parts'
    }

    if(ipArr.find(ele=>+ele<0||+ele>255)){
        return "a valid IP has 4 numerical parts is not less then 0 and no more then 255"
    }
    if (ipArr.find(ele => ele.length > 1 && +ele[0] === 0)){
        return `the first part of an IPv4 address cannot be zero`
    }

    return input
}

module.exports = validateIp

// input = '192..0.1'
// const test = input.split('.')

// console.log(test)


app.test.js


const validateIp = require('../app')


describe("validateIp", ()=>{
    it('Should output undefined if no input is passed through', ()=>{
        let emptyIp;
        const result = validateIp(emptyIp)
        expect(result).toBeUndefined()
        expect(result).toBeFalsy()
        expect(result).toEqual(undefined)
    })
    it("Should output an error message if the IP address doesn't contain enough parts", ()=>{
        let testIp = '192.168.0';
        const result = validateIp(testIp)
        
        expect (result).toBeTruthy()
        expect (result).toEqual('There are 4 parts to a valid IP Address')
    })
    it("Should output an error message if the IP address contains an empty part", ()=>{
        let testIp = '192..0.1';
        const result = validateIp(testIp)
        
        expect (result).toBeTruthy()
        expect (result).toEqual('a valid IP has 4 numerical parts')
    })
    it("Should output an error message if the IP address less then 0 or greater then 255", ()=>{
        let testIp = '192.257.1.1';
        const result = validateIp(testIp)
        
        expect (result).toBeTruthy()
        expect (result).toEqual('a valid IP has 4 numerical parts is not less then 0 and no more then 255')
    })
    it("Should output an error message if the IP address contains a leading 0", ()=>{
        let testIp = '192.001.0.1';
        const result = validateIp(testIp)
        
        expect (result).toBeTruthy()
        expect(result).toEqual('the first part of an IPv4 address cannot be zero')
    })
    it("Should return IP if valid", ()=>{
        let testIp = '192.121.223.112';
        const result = validateIp(testIp)
        
        expect (result).toBeTruthy()
        expect(result).toEqual(testIp)
    })
})